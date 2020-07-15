# Account API

## Get account info

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://api.sirv.com/v2/account');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'authorization' => 'Bearer BEARER_TOKEN'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://api.sirv.com/v2/account"

payload = ""
headers = {'authorization': 'Bearer BEARER_TOKEN'}

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.sirv.com/v2/account \
  --header 'authorization: Bearer BEARER_TOKEN'
```

```javascript
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "path": "/v2/account",
  "headers": {
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

req.end();
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/account")
  .header("authorization", "Bearer BEARER_TOKEN")
  .asString();
```

> The above command returns JSON structured like this:

```json
{
  "dateCreated": "2019-12-04T16:10:17.639Z",
  "alias": "test1",
  "fileSizeLimit": 33554432,
  "aliases": {
    "test1": {
      "prefix": "/"
    }
  },
  "fetching": {
    "maxFilesize": 3145728
  }
}
```

Use this API method to get information about the account, including its CDN URL; account name; additional domains; remote fetching status; date created and more.

### HTTP Request

```http
GET /v2/account HTTP/1.1
Authorization: Bearer BEARER_TOKEN
Host: api.sirv.com
```

### Query Parameters

None

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

