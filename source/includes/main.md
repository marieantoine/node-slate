# Introduction

Welcome to official documentation for the TireCoop API!

If you are a registered TireCoop Vendor, the TireCoop API provides access to endpoints that allow you to search for Dealers that are part of your program and to place orders to against the Dealers.


# Authentication

> To authorize, use this code:

```csharp
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```


> Make sure to replace `meowmeowmeow` with your API key.

TireCoop uses API keys to provide authenticated access to the API. Once registered as a Vendor, you can contact us for a key at [support@esprofessionals.com](mailto:support@esprofessionals.com).

TireCoop requires developers to send the authorization containing their API keys for all endpoints in the header.

<!-- `Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside> -->

# Search API

## Get Closest Dealers
<!-- 
```csharp
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
``` -->

> A request returns JSON structured like this:

```json
[
  {
      "id": "4c164234-69ec-44c3-8354-111eec13337d",
      "name": "Wheel Demo",
      "email": "wheeldemo@tirewire.com",
      "phone": "0000000000",
      "address": "1211a Lexington Ave, New York, NY 10028, USA",
      "latitude": 40.7769914,
      "longitude": -73.957262599999979,
      "services": null,
      "theming": null,
      "warehouses": null
  },
  {
      "id": "4c6dcdd5-f628-4c77-9eca-c71db1e538cd",
      "name": "Mike's New Tire Shop",
      "email": "161083.toolbox@tirewire.com",
      "phone": "205615322",
      "address": "5th Ave, New York, NY, USA",
      "latitude": 40.774414599999993,
      "longitude": -73.9656177,
      "services": null,
      "theming": null,
      "warehouses": null
  }
]
```

This endpoint retrieves closest dealers within a radius.

### HTTP Request

`GET http://api.tiremove.com/api/search`

### Query Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
size | 5 | No | If not set to anything, the result will return the five closest dealers.
radius | 10 | Yes | If not set to anything, the result will include results within the first 50 km from the location specified.
lat | - | Yes | This is the latitude coordinate of the customer's location.
lng | - | Yes | This is the longitude coordinate of the customer's location.

<!-- <aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside> -->

<!-- ## Get a Specific Kitten

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

```bash
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
ID | The ID of the kitten to retrieve -->


# Orders API

## Create Order

> The POST request JSON would be structured like this:

```json
{
  "vendorId": "abcdefg1234567dbca054c3c07078cd",
  "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
  "warehouseId": 17,
  "customer": {
    "email": "carolinetest@example.com",
    "name": "Caroline",
    "phone": "555-5555-5555"
  },
  "paymentReference": "CUST-384903",
  "items": [
    {
      "tireId": 11,
      "quantity": 2,
      "price": 49,
      "tax": 11.33
    }
  ]
}

```
This endpoint creates a TireCoop Order that is then sent to the Vendor and Dealer tools.

### HTTP Request

`POST http://api.tiremove.com/api/search`

### Query Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
vendorId | 5 | No | -
dealerId | 10 | Yes | -
warehouseId | - | Yes | -
customer | - | Yes | -
paymentReference | | |
items | | |