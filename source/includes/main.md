# Introduction

Welcome to official documentation for the TireCoop API!

If you are a registered TireCoop Vendor, the TireCoop API provides access to endpoints that allow you to search for Dealers that are part of your program and to place orders to against the Dealers.


<!-- # Authentication -->

<!-- > To authorize, use this code:

```csharp
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```


> Make sure to replace `meowmeowmeow` with your API key. -->
<!-- 
TireCoop uses API keys to provide authenticated access to the API. Once registered as a Vendor, you can contact us for a key at [support@esprofessionals.com](mailto:support@esprofessionals.com).

TireCoop requires developers to send the authorization containing their API keys for all endpoints in the header. -->

<!-- `Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside> -->

# Search API

## Get Closest Dealers

```csharp

 HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("http://api.tiremove.com/")
    }

    client.DefaultRequestHeaders.Add("bearer", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("api/search?size=10&radius=15&lat=40.77&lng=-73.95"));

```

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
radius | - | Yes | All dealer results will be within this specified radius.
lat | - | Yes | This is the latitude coordinate of the customer's location.
lng | - | Yes | This is the longitude coordinate of the customer's location.

## Get Dealer Services

This endpoint retrieves the services of a specific dealer.

### HTTP Request

`GET http://api.tiremove.com/api/search/{dealerid}/services`

### Query Parameters

Parameter | Required | Description
--------- | -------- | ----------- 
dealerid | Yes | The results will return the services for this particular dealer.

```csharp

 HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("http://api.tiremove.com/")
    }

    client.DefaultRequestHeaders.Add("bearer", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("api/search/{dealerid}/services"));

```

>The following sample represents the JSON response for this endpoint:

```json
{
  "name": "Best Tire",
  "price": 60.00,
  "description": "Tire Fitting"
}
```

# Orders API

## Create Order

> The following sample represents the JSON response for this endpoint:

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

`POST http://api.tiremove.com/api/orders`

### Query Parameters

Parameter | Description
--------- | -----------
vendorId | The identifier of the site vendor.
dealerId | The identifier of the dealer chosen by the customer.
warehouseId | The warehouse number
customer | The customer details including this name, email and phone number.
paymentReference | The payment reference of the transaction (this could reflect the Transaction No from treadsearch)
items | The items bought by the customer, including the tirelibrary TireID, the quantity, the price and the tax
