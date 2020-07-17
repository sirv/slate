## Search files

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/search", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url https://api.sirv.com/v2/files/search \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '{"query":"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash","from":0,"size":5}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/search",
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

req.write("{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}");
req.end();
```

```javascript
var data = "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/search");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/search")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/search",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}",
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

Use this API method to search for files with a certain name, location, extension, type, created/modified time or with some specific meta information.

### Query string


None


### Body payload


<div class="center-column"></div>

```json
{
  "type": "object",
  "properties": {
    "query": {
      "examples": [
        "extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash"
      ],
      "example": "extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash",
      "type": "string",
      "maxLength": 1024
    },
    "sort": {
      "examples": [
        {
          "filename.raw": "asc"
        }
      ],
      "example": {
        "filename.raw": "asc"
      },
      "type": "object",
      "properties": {},
      "additionalProperties": true,
      "patterns": []
    },
    "from": {
      "examples": [
        0
      ],
      "example": 0,
      "type": "number",
      "maximum": 1000
    },
    "size": {
      "examples": [
        5
      ],
      "example": 5,
      "type": "number",
      "maximum": 100
    },
    "scroll": {
      "description": "Start a scrolling search.",
      "type": "boolean"
    }
  },
  "additionalProperties": false,
  "patterns": []
}
```


### Response

Example response:

```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 15:39:25 GMT
< content-type: application/json; charset=utf-8
< content-length: 5322
< connection: close
< x-ratelimit-limit: 1000
< x-ratelimit-remaining: 994
< x-ratelimit-reset: 1595003237
< x-ratelimit-type: rest:post:files:search
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "hits": [
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "4b57cdf35a3568220bb9ad7a6f62f0048c8b4ae1",
      "_score": 1.1882421,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/aurora.jpg",
        "dirname": "/REST API Examples",
        "basename": "aurora.jpg",
        "extension": ".jpg",
        "id": "tkLbo0YuHJuBIEYj40lEUYRZZ8cLBGnF",
        "ctime": "2020-07-17T13:31:39.348Z",
        "mtime": "2020-07-17T13:31:39.464Z",
        "size": 788807,
        "contentType": "image/jpeg",
        "meta": {
          "width": 2500,
          "height": 1667,
          "format": "JPEG",
          "duration": 0,
          "EXIF": {
            "ModifyDate": "2020-01-29T17:12:45Z"
          }
        }
      },
      "sort": [
        1.1882421,
        "/REST API Examples/aurora.jpg",
        ".jpg"
      ]
    },
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "ac9224d68ecaa7e6b2b2ddbd840190c190391db2",
      "_score": 1.1882421,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/birdbath.jpg",
        "dirname": "/REST API Examples",
        "basename": "birdbath.jpg",
        "extension": ".jpg",
        "id": "Husg8zi0IBla2fl98FjTvc16ojcKm0TR",
        "ctime": "2020-07-17T13:31:39.348Z",
        "mtime": "2020-07-17T13:31:39.385Z",
        "size": 73151,
        "contentType": "image/jpeg",
        "meta": {
          "width": 620,
          "height": 372,
          "format": "JPEG",
          "duration": 0
        }
      },
      "sort": [
        1.1882421,
        "/REST API Examples/birdbath.jpg",
        ".jpg"
      ]
    },
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "1b86315bcaadbc77626f40f0bf9e2ed63c370194",
      "_score": 1.1882421,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/blue-lake.jpg",
        "dirname": "/REST API Examples",
        "basename": "blue-lake.jpg",
        "extension": ".jpg",
        "id": "t8b6TbESDLYThXazo9KUCGWilVXq6fOo",
        "ctime": "2020-07-17T13:31:39.347Z",
        "mtime": "2020-07-17T13:31:39.450Z",
        "size": 587065,
        "contentType": "image/jpeg",
        "meta": {
          "title": "Blue Lake",
          "description": "Blue Lake in the Winter",
          "tags": [
            "blue",
            "lake",
            "winter",
            "cold",
            "water"
          ],
          "width": 1578,
          "height": 1002,
          "format": "JPEG",
          "duration": 0,
          "EXIF": {
            "DateTimeOriginal": "2018-01-01T13:57:00Z",
            "CreateDate": "2018-01-01T13:57:00Z",
            "ModifyDate": "2018-01-02T19:26:34Z",
            "ImageDescription": "cof",
            "Make": "HUAWEI",
            "Model": "EVA-L09"
          }
        }
      },
      "sort": [
        1.1882421,
        "/REST API Examples/blue-lake.jpg",
        ".jpg"
      ]
    },
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "57c6df356e0db18178a2b188ff0c2f8c352d7efe",
      "_score": 1.1882421,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/coin/coin_01.jpg",
        "dirname": "/REST API Examples/coin",
        "basename": "coin_01.jpg",
        "extension": ".jpg",
        "id": "kkzhuxEQEVixRk6o4G1QjrQ0ih0VGVNi",
        "ctime": "2020-07-17T13:31:08.874Z",
        "mtime": "2020-07-17T13:31:08.893Z",
        "size": 135255,
        "contentType": "image/jpeg",
        "meta": {
          "width": 1056,
          "height": 1056,
          "format": "JPEG",
          "duration": 0,
          "EXIF": {
            "ModifyDate": "2018-02-03T17:12:43Z",
            "ColorSpace": "Uncalibrated"
          }
        }
      },
      "sort": [
        1.1882421,
        "/REST API Examples/coin/coin_01.jpg",
        ".jpg"
      ]
    },
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "d4cadbf0969a407d918852f43800168d6199a98c",
      "_score": 1.1882421,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/coin/coin_02.jpg",
        "dirname": "/REST API Examples/coin",
        "basename": "coin_02.jpg",
        "extension": ".jpg",
        "id": "BL67essSx34CvO3XM7GddBvqphbHAvti",
        "ctime": "2020-07-17T13:31:08.874Z",
        "mtime": "2020-07-17T13:31:08.994Z",
        "size": 141482,
        "contentType": "image/jpeg",
        "meta": {
          "width": 1056,
          "height": 1056,
          "format": "JPEG",
          "duration": 0,
          "EXIF": {
            "ModifyDate": "2018-02-03T17:12:45Z",
            "ColorSpace": "Uncalibrated"
          }
        }
      },
      "sort": [
        1.1882421,
        "/REST API Examples/coin/coin_02.jpg",
        ".jpg"
      ]
    }
  ],
  "total": 9918,
  "_relation": "eq"
}
```
