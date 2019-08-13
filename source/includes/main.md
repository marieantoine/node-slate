# Introduction

Welcome to official documentation for the TireCoop API!

If you are a registered TireCoop Vendor, the TireCoop API provides access to endpoints that allow you to geolocate dealers that are part of your program and to send order confirmations against the dealers, effectively helping you to streamline the management of your orders.


# Authentication

TireCoop uses API keys to provide authenticated access to the API. You can contact us for a key at [support@esprofessionals.com](mailto:support@esprofessionals.com).

TireCoop requires developers to send the authorization containing their API keys for all endpoints in the header. 
<aside class="notice">
You must replace <code>YourApiKeyHere</code> with your personal API key.
</aside>


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
        (await client.GetStringAsync("api/search?vendorId=abcdefg1234567dbca054c3c07078cd&size=10&radius=15&lat=40.77&lng=-73.95"));

```

> A request returns JSON structured like this:

```json
[
    {
        "id": "e3baffffd56f4d5f9d0e8e579a98c0dc",
        "name": "Caroline Wheels",
        "email": "caroline@esprofessionals.com",
        "phone": "245879632",
        "address": "Tesla Rd, Livermore, CA 94550, USA",
        "restrictions": "No restrictions under 22 wheel diameters.",
        "about": "Founded in 1998, Caroline Tires shop has been selling and providing excellent services to their customers.",
        "contactName": "Maria",
        "contactMobile": "500194855",
        "contactPosition": "Manager",
        "latitude": 37.665115,
        "longitude": -121.71895599999999,
        "services": null,
        "theming": {
            "logoUrl": "https://api.tiremove.com/images/387b6bc6-1b58-478a-90b3-be3e58a39bf5.png",
            "shortLogoUrl": null,
            "coverPhotoUrl": null,
            "storePhotoUrls": null
        },
        "openingHours": [
            {
                "day": "Monday",
                "openingHour": "09:00",
                "closingHour": "17:00"
            },
            {
                "day": "Tuesday",
                "openingHour": "09:00",
                "closingHour": "20:00"
            },
            {
                "day": "Wednesday",
                "openingHour": "09:00",
                "closingHour": "17:00"
            },
            {
                "day": "Thursday",
                "openingHour": "08:00",
                "closingHour": "18:00"
            },
            {
                "day": "Friday",
                "openingHour": "08:00",
                "closingHour": "17:00"
            },
            {
                "day": "Saturday",
                "openingHour": "11:30",
                "closingHour": "15:30"
            },
            {
                "day": "Sunday",
                "openingHour": "10:00",
                "closingHour": "15:30"
            }
        ],
        "warehouses": [
            {
                "id": 1,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "warehouseId": 17,
                "warehouse": {
                    "id": 17,
                    "name": "Warehouse 2",
                    "email": "warehouse@tiremove.com",
                    "phone": "555-555-554",
                    "address": "675 Boylston St, Boston, MA 02116, USA",
                    "latitude": 0.0,
                    "longitude": 0.0,
                    "location": {
                        "latitude": 0.0,
                        "longitude": 0.0
                    },
                    "distance": 0.0,
                    "connectionId": 24318,
                    "vendorId": "abcdefg1234567dbca054c3c07078cd",
                    "vendor": null,
                    "createdAt": "2018-08-16T03:35:27.1490834",
                    "isActive": true,
                    "dealers": null
                },
                "isActive": true
            }
        ],
        "accreditations": [
            {
                "id": 81,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "accreditationId": 1,
                "accreditation": {
                    "id": 0,
                    "name": "ASE"
                }
            },
            {
                "id": 82,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "accreditationId": 2,
                "accreditation": {
                    "id": 0,
                    "name": "TIA"
                }
            }
        ],
        "installations": [
            {
                "id": 165,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 2,
                "installation": {
                    "id": 0,
                    "name": "50-55 Series"
                },
                "price": 26.0
            },
            {
                "id": 166,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 10,
                "installation": {
                    "id": 0,
                    "name": "TPMS Surcharge"
                },
                "price": 0.0
            },
            {
                "id": 167,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 9,
                "installation": {
                    "id": 0,
                    "name": "LT Size Surcharge"
                },
                "price": 0.0
            },
            {
                "id": 168,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 1,
                "installation": {
                    "id": 0,
                    "name": "60 Series and higher"
                },
                "price": 15.0
            },
            {
                "id": 169,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 8,
                "installation": {
                    "id": 0,
                    "name": "21\" and Above Add"
                },
                "price": 0.0
            },
            {
                "id": 170,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 3,
                "installation": {
                    "id": 0,
                    "name": "40-45 Series"
                },
                "price": 33.0
            },
            {
                "id": 171,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 4,
                "installation": {
                    "id": 0,
                    "name": "35 Series and lower"
                },
                "price": 24.32
            },
            {
                "id": 172,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 5,
                "installation": {
                    "id": 0,
                    "name": "Rubber Valve Stems"
                },
                "price": 15.0
            },
            {
                "id": 173,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 6,
                "installation": {
                    "id": 0,
                    "name": "Disposal Fee"
                },
                "price": 10.0
            },
            {
                "id": 174,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "installationId": 7,
                "installation": {
                    "id": 0,
                    "name": "Run-Flat Surcharge"
                },
                "price": 0.0
            }
        ],
        "vehicles": [
            {
                "id": 187,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "vehicleTypeId": 5,
                "vehicleType": {
                    "id": 0,
                    "name": "Industrial"
                }
            },
            {
                "id": 188,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "vehicleTypeId": 3,
                "vehicleType": {
                    "id": 0,
                    "name": "Medium Truck"
                }
            },
            {
                "id": 189,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "vehicleTypeId": 4,
                "vehicleType": {
                    "id": 0,
                    "name": "Farm"
                }
            },
            {
                "id": 190,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "vehicleTypeId": 1,
                "vehicleType": {
                    "id": 0,
                    "name": "Passenger"
                }
            },
            {
                "id": 191,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "vehicleTypeId": 6,
                "vehicleType": {
                    "id": 0,
                    "name": "Commercial"
                }
            },
            {
                "id": 192,
                "dealerId": "e3baffffd56f4d5f9d0e8e579a98c0dc",
                "vehicleTypeId": 7,
                "vehicleType": {
                    "id": 0,
                    "name": "ATV/UTV"
                }
            }
        ],
        "averageRating": 4.333333333333333
    }
]
```

This endpoint retrieves closest dealers within a radius.

### HTTP Request

`GET http://api.tiremove.com/api/search`

### Query Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- | -----------
vendorId | - | Yes | This is the identifier of the site vendor.
size | 5 | No | If not set to anything, the result will return the five closest dealers.
radius | - | Yes | All dealer results will be within this specified radius.
lat | - | Yes | This is the latitude coordinate of the customer's location.
lng | - | Yes | This is the longitude coordinate of the customer's location.


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
