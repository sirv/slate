## Mark account event(s) as seen

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "[\"f1f5d68ef232e5d27d10f28bcef836efbb7cdeba\",\"199cf48046964f8567fe49e22107c4c5d27271e7\"]"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/account/events/seen", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/account/events/seen \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '["f1f5d68ef232e5d27d10f28bcef836efbb7cdeba","199cf48046964f8567fe49e22107c4c5d27271e7"]'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/account/events/seen",
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

req.write("[\"f1f5d68ef232e5d27d10f28bcef836efbb7cdeba\",\"199cf48046964f8567fe49e22107c4c5d27271e7\"]");
req.end();
```

```javascript
var data = "[\"f1f5d68ef232e5d27d10f28bcef836efbb7cdeba\",\"199cf48046964f8567fe49e22107c4c5d27271e7\"]";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/account/events/seen");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/account/events/seen")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("[\"f1f5d68ef232e5d27d10f28bcef836efbb7cdeba\",\"199cf48046964f8567fe49e22107c4c5d27271e7\"]")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/account/events/seen",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "[\"f1f5d68ef232e5d27d10f28bcef836efbb7cdeba\",\"199cf48046964f8567fe49e22107c4c5d27271e7\"]",
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

url = URI("https://api.sirv.com/v2/account/events/seen")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "[\"f1f5d68ef232e5d27d10f28bcef836efbb7cdeba\",\"199cf48046964f8567fe49e22107c4c5d27271e7\"]"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "["f1f5d68ef232e5d27d10f28bcef836efbb7cdeba","199cf48046964f8567fe49e22107c4c5d27271e7"]".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/account/events/seen")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/account/events/seen");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "[\"f1f5d68ef232e5d27d10f28bcef836efbb7cdeba\",\"199cf48046964f8567fe49e22107c4c5d27271e7\"]", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/account/events/seen"

	payload := strings.NewReader("[\"f1f5d68ef232e5d27d10f28bcef836efbb7cdeba\",\"199cf48046964f8567fe49e22107c4c5d27271e7\"]")

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

Add `seen` flag for specified account event(s)

### Query string


None


### Body payload


Example:

<div class="center-column"></div>
```json
[
  "f1f5d68ef232e5d27d10f28bcef836efbb7cdeba",
  "199cf48046964f8567fe49e22107c4c5d27271e7"
]
```




JSON Schema:

<div class="center-column"></div>
```json
{
  "examples": [
    [
      "f1f5d68ef232e5d27d10f28bcef836efbb7cdeba",
      "199cf48046964f8567fe49e22107c4c5d27271e7"
    ]
  ],
  "example": [
    "f1f5d68ef232e5d27d10f28bcef836efbb7cdeba",
    "199cf48046964f8567fe49e22107c4c5d27271e7"
  ],
  "type": "array",
  "maxItems": 100,
  "items": {
    "type": "string"
  }
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Tue, 21 Jul 2020 09:17:41 GMT
< content-length: 0
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6982
< x-ratelimit-reset: 1595326565
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

/ no response body: HTTP status 200 means SUCCESS /
```
