## Get users

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("GET", "/v2/account/users", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://api.sirv.com/v2/account/users \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json'
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/account/users",
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

xhr.open("GET", "https://api.sirv.com/v2/account/users");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/account/users")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/account/users",
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

Use this API method to get a list of all users of an account. It will return a list of user IDs and their roles. If you need a users email address, the user ID can be used to obtain it.

### Query string


None


### Body payload


None


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 16:36:55 GMT
< content-type: application/json; charset=utf-8
< content-length: 833
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6966
< x-ratelimit-reset: 1595006894
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< accept-ranges: bytes
< server: Sirv.API
< strict-transport-security: max-age=31536000

[
  {
    "role": "primaryOwner",
    "userId": "VrY0MFX1Bc3hxEG5tjPQSx6H5z3"
  },
  {
    "role": "owner",
    "userId": "aHhi4gGjBvJJtCTdwa4q9CxD7lD"
  },
  {
    "role": "owner",
    "userId": "9fyQAGrdSN5GH7Wr8fZ9LOB6EXY"
  },
  {
    "role": "contributor",
    "userId": "Sy4A2dlgTG0h1ONsbw2HWTsxaXa"
  },
  {
    "role": "admin",
    "userId": "L5UwRaLpSScHgnuhaocj0QpyYQG"
  },
  {
    "role": "owner",
    "userId": "Ph8DDPLv4HnoLSf1qz60melOryN"
  },
  {
    "role": "user",
    "userId": "UH9C80LsMj59doRAMIEsLHptOMe"
  },
  {
    "role": "user",
    "userId": "3nFhREbVRu3iqq5uVaIx1dXEoMj"
  },
  {
    "role": "user",
    "userId": "XhkYgmOGHgSdk07dLy4a4hztbVW"
  },
  {
    "role": "contributor",
    "userId": "VERvVsOKXc8kSMWq3Cq3gCaWapN"
  },
  {
    "role": "viewer",
    "userId": "Gt6ljl1AxwmtGBIHX0WBo3qKdtK"
  }
]
```
