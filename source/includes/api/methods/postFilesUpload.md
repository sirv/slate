## Upload file

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = open('/path/to/local-image.jpg', 'rb')

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/upload?filename=%2Fpath%2Fto%2Fuploaded-image.jpg", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
 --url 'https://api.sirv.com/v2/files/upload?filename=%2Fpath%2Fto%2Fuploaded-image.jpg' \\
 --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
 --header 'content-type: image/jpeg'  \\
 --data "@/path/to/local-file.jpg"
```

```javascript--node
var http = require("https");
var fs = require("fs");

fs.readFile('/path/to/local-image.jpg', (err, fileData) => {
  if (err) throw err;


  var options = {
    "method": "POST",
    "hostname": "api.sirv.com",
    "port": null,
    "path": "/v2/files/upload?filename=%2Fpath%2Fto%2Fuploaded-image.jpg",
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

  req.write(fileData);
  req.end();

});
```

Use this API method to upload a single file to an account. It is an alternative to the S3 API file upload method (see the S3 API documentation).

### Query string


Parameter | Type | Description | Example
--------- | ---- | ----------- | -------
filename | string |  | /REST API Examples/uploaded.txt


### Body payload

Binary file contents.

### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Sat, 18 Jul 2020 11:46:06 GMT
< content-length: 0
< connection: close
< x-ratelimit-limit: 2000
< x-ratelimit-remaining: 1996
< x-ratelimit-reset: 1595075494
< x-ratelimit-type: rest:post:files:upload
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

/ no response body: HTTP status 200 means SUCCESS /
```
