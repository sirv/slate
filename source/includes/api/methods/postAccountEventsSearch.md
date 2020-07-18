## List or search account events

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"module\":\"fetching\"}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/account/events/search", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url https://api.sirv.com/v2/account/events/search \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '{"module":"fetching"}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/account/events/search",
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

req.write("{\"module\":\"fetching\"}");
req.end();
```

```javascript
var data = "{\"module\":\"fetching\"}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/account/events/search");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/account/events/search")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"module\":\"fetching\"}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/account/events/search",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"module\":\"fetching\"}",
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

url = URI("https://api.sirv.com/v2/account/events/search")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"module\":\"fetching\"}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"module":"fetching"}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/account/events/search")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/account/events/search");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"module\":\"fetching\"}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/account/events/search"

	payload := strings.NewReader("{\"module\":\"fetching\"}")

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

List all events triggered for account.

### Query string


None


### Body payload


JSON Schema:

<div class="center-column"></div>
```json
{
  "type": "object",
  "properties": {
    "module": {
      "examples": [
        "fetching"
      ],
      "example": "fetching",
      "type": "string",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "maxLength": 64
    },
    "filename": {
      "type": "string",
      "maxLength": 1000
    },
    "level": {
      "enum": [
        "error",
        "warn",
        "info"
      ],
      "type": "string"
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
< date: Sat, 18 Jul 2020 09:03:35 GMT
< content-type: application/json; charset=utf-8
< content-length: 2742
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6718
< x-ratelimit-reset: 1595064951
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< server: Sirv.API
< strict-transport-security: max-age=31536000

[
  {
    "module": "fetching",
    "type": "http",
    "level": "error",
    "filename": "/REST API Examples/missing.jpg",
    "fetching": {
      "url": "https://demo.sirv.com/missing.jpg",
      "statusCode": 404,
      "maxFilesize": 2097152,
      "contentLength": "4140",
      "error": "Request not successful: expected status code 200 but got 404"
    },
    "initiator": {
      "type": "api",
      "remoteAddr": "176.105.166.4",
      "date": "2020-07-18T08:55:32.120Z"
    },
    "notify": true,
    "_seen": false,
    "_submitted": "2020-07-18T08:55:32.882Z",
    "_accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
    "_id": "f17b058ec4bffa22a164a31cf87b252ca4329754"
  }
]
```
