## Get user info

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("GET", "/v2/user?userId=Gt6ljl1AxwmtGBIHX0WBo3qKdtK", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url 'https://api.sirv.com/v2/user?userId=Gt6ljl1AxwmtGBIHX0WBo3qKdtK' \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json'
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/user?userId=Gt6ljl1AxwmtGBIHX0WBo3qKdtK",
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

xhr.open("GET", "https://api.sirv.com/v2/user?userId=Gt6ljl1AxwmtGBIHX0WBo3qKdtK");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/user?userId=Gt6ljl1AxwmtGBIHX0WBo3qKdtK")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/user?userId=Gt6ljl1AxwmtGBIHX0WBo3qKdtK",
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

Use this API method to get information about a user, including their name, email and S3 key.

### Query string


Parameter | Type | Description | Example
--------- | ---- | ----------- | -------
userId | string |  | Gt6ljl1AxwmtGBIHX0WBo3qKdtK


### Body payload


None


### Response

Example response:

<div class="center-column"></div>

```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 16:23:39 GMT
< content-type: application/json; charset=utf-8
< content-length: 188
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6819
< x-ratelimit-reset: 1595003234
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< accept-ranges: bytes
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "email": "restapi@sirv.com",
  "firstName": "Rest",
  "lastName": "Api",
  "dateCreated": "2020-07-17T13:55:10.462Z",
  "s3Secret": "**********************************"
}
```
