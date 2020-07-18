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
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/account/limits",
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

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/account/limits",
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
< date: Sat, 18 Jul 2020 09:51:48 GMT
< content-type: application/json; charset=utf-8
< content-length: 2892
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6893
< x-ratelimit-reset: 1595068849
< x-ratelimit-type: rest:global
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
    "reset": 1595069508
  },
  "s3:PUT": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595069508
  },
  "s3:GET": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595069508
  },
  "s3:DELETE": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595069508
  },
  "rest:global": {
    "count": 107,
    "limit": 7000,
    "remaining": 6893,
    "reset": 1595068849
  },
  "rest:post:files:search": {
    "count": 3,
    "limit": 1000,
    "remaining": 997,
    "reset": 1595068855
  },
  "rest:post:files:search:scroll": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595069508
  },
  "rest:post:files:video2spin": {
    "count": 3,
    "limit": 200,
    "remaining": 197,
    "reset": 1595068855
  },
  "rest:post:files:spin2video": {
    "count": 3,
    "limit": 200,
    "remaining": 197,
    "reset": 1595068858
  },
  "rest:post:files:fetch": {
    "count": 3,
    "limit": 2000,
    "remaining": 1997,
    "reset": 1595068863
  },
  "rest:post:files:upload": {
    "count": 9,
    "limit": 2000,
    "remaining": 1991,
    "reset": 1595066135
  },
  "rest:post:files:delete": {
    "count": 3,
    "limit": 3000,
    "remaining": 2997,
    "reset": 1595068867
  },
  "rest:post:account": {
    "count": 4,
    "limit": 50,
    "remaining": 46,
    "reset": 1595068850
  },
  "rest:post:account:fetching": {
    "count": 0,
    "limit": 50,
    "remaining": 50,
    "reset": 1595069508
  },
  "rest:get:stats:http": {
    "count": 3,
    "limit": 100,
    "remaining": 97,
    "reset": 1595068851
  },
  "rest:get:stats:storage": {
    "count": 3,
    "limit": 100,
    "remaining": 97,
    "reset": 1595068852
  },
  "rest:post:account:new": {
    "count": 0,
    "limit": 5,
    "remaining": 5,
    "reset": 1595069508
  },
  "rest:post:user:accounts": {
    "count": 0,
    "limit": 20,
    "remaining": 20,
    "reset": 1595069508
  },
  "rest:get:rest:credentials": {
    "count": 0,
    "limit": 50,
    "remaining": 50,
    "reset": 1595069508
  },
  "rest:post:video:toSpin": {
    "count": 0,
    "limit": 400,
    "remaining": 400,
    "reset": 1595069508
  },
  "rest:post:upload:toSirv": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595069508
  },
  "ftp:global": {
    "count": 0,
    "limit": 10000,
    "remaining": 10000,
    "reset": 1595069508
  },
  "ftp:STOR": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595069508
  },
  "ftp:RETR": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595069508
  },
  "ftp:DELE": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595069508
  },
  "fetch:file": {
    "count": 1,
    "limit": 2000,
    "remaining": 1999,
    "reset": 1595068863
  }
}
```
