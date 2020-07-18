## Get spins views

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("GET", "/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \\
  --url 'https://api.sirv.com/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000' \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json'
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000",
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

xhr.open("GET", "https://api.sirv.com/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000",
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

url = URI("https://api.sirv.com/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000")

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

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000");
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

	url := "https://api.sirv.com/v2/stats/spins/views?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000"

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

Use this API method to get spins views stats over a certain period (date from/to). Date range is limited to 5 days.

### Query string


Parameter | Type | Description | Example
--------- | ---- | ----------- | -------
from | date | Default: 1 day ago | 2020-07-01T00:00:00.000
to | date | Default: now | 2020-07-05T00:00:00.000
alias | string | Filter by account name (alias) |


### Body payload


None


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Sat, 18 Jul 2020 11:32:15 GMT
< content-type: application/json; charset=utf-8
< content-length: 4286915
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6955
< x-ratelimit-reset: 1595075478
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< accept-ranges: bytes
< server: Sirv.API
< strict-transport-security: max-age=31536000

[
  {
    "@timestamp": "2020-07-04T03:51:03.792Z",
    "referer": "https://demo.sirv.com/cap.spin",
    "user_agent": "Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.118 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)",
    "user_agent_parsed": {
      "name": "Googlebot",
      "os": "Android 6.0.1",
      "os_name": "Android",
      "os_major": "6",
      "os_minor": "0",
      "device": "Spider",
      "major": "2",
      "minor": "1"
    },
    "referer_proto": "https",
    "referer_host": "demo.sirv.com",
    "referer_uripath": "/cap.spin",
    "event": {
      "origin": "/cap.spin",
      "type": "spin",
      "name": "viewerReady",
      "data": {
        "rows": 1,
        "columns": 24,
        "viewerSize": {
          "width": 412,
          "height": 732
        }
      }
    },
    "geoip": {
      "country_code2": "US",
      "country_name": "United States",
      "region_name": "CA",
      "timezone": "America/Los_Angeles",
      "real_region_name": "California"
    }
  }
]
```
