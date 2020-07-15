## Update account info

```python
import requests

url = "https://api.sirv.com/v2/account"

payload = "{\n\t\"fetching\": {\n\t\t\"enabled\": false,\n\t\t\"type\": \"http\",\n\t\t\"http\": {\n\t\t\t\"url\": \"https://mysite.com\"\n\t\t}\n\t},\n\t\"minify\": {\n\t\t\"enabled\": false\n\t},\n\t\"aliases\": {\n\t\t\"test1\": {\n\t\t\t\"prefix\": \"/\"\t\t\t\n\t\t}\n\t}\n}"
headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url https://api.sirv.com/v2/account \
  --header 'authorization: Bearer BEARER_TOKEN' \
  --header 'content-type: application/json' \
  --data '{
  "fetching": {
    "enabled": false,
    "type": "http",
    "http": {
      "url": "https://mysite.com"
    }
  },
  "minify": {
    "enabled": false
  },
  "aliases": {
    "test1": {
      "prefix": "/"
    }
  }
}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/account",
  "headers": {
    "content-type": "application/json",
    "authorization": "Bearer BEARER_TOKEN"
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

req.write(JSON.stringify({
  fetching: {enabled: false, type: 'http', http: {url: 'https://mysite.com'}},
  minify: {enabled: false},
  aliases: {test1: {prefix: '/'}}
}));
req.end();
```

```javascript
var data = JSON.stringify({
  "fetching": {
    "enabled": false,
    "type": "http",
    "http": {
      "url": "https://mysite.com"
    }
  },
  "minify": {
    "enabled": false
  },
  "aliases": {
    "test1": {
      "prefix": "/"
    }
  }
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/account");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/account")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN")
  .body("{\n\t\"fetching\": {\n\t\t\"enabled\": false,\n\t\t\"type\": \"http\",\n\t\t\"http\": {\n\t\t\t\"url\": \"https://mysite.com\"\n\t\t}\n\t},\n\t\"minify\": {\n\t\t\"enabled\": false\n\t},\n\t\"aliases\": {\n\t\t\"test1\": {\n\t\t\t\"prefix\": \"/\"\t\t\t\n\t\t}\n\t}\n}")
  .asString();
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
  "fetching": {
    "enabled": false,
    "type": "http",
    "http": {
      "url": "https://mysite.com"
    }
  },
  "minify": {
    "enabled": false
  },
  "aliases": {
    "test1": {
      "prefix": "/"
    }
  }
}');

$request->setRequestUrl('https://api.sirv.com/v2/account');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'content-type' => 'application/json',
  'authorization' => 'Bearer BEARER_TOKEN'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```http
POST /v2/account HTTP/1.1
Content-Type: application/json
Authorization: Bearer BEARER_TOKEN
Host: api.sirv.com

{
  "fetching": {
    "enabled": false,
    "type": "http",
    "http": {
      "url": "https://mysite.com"
    }
  },
  "minify": {
    "enabled": false
  },
  "aliases": {
    "test1": {
      "prefix": "/"
    }
  }
}
```

Use this method to change the account options. You can enable or disable JS/CSS file minification. You can also enable/disable automatic fetching via HTTP or S3 from a remote location.

<aside class="warning">Be carefull when changing account options.</aside>

### URL Parameters

None

### Response

There is no response body. This method will return HTTP status code 200 on success.
