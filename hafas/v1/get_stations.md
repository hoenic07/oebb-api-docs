# GET /hafas/v1/stations

Find stations by name or location.

## URL

```HTTP
GET https://tickets.oebb.at/api/hafas/v1/stations
```

## Headers

``` HTTP
AccessToken: <your access token>
x-ts-supportid: 1
Channel: inet
```

Use the [Authentication endpoint](../../domain/v4/get_init.md) to generate the access token.

## Query Parameters

* `count`: Optional. No. of results. Behaves randomly, dependent on the search. Sometimes it works, sometimes not.

### Search by Station Name

* `name`: e.g.: `Wien`

### Search by Location

* `longitude`: e.g. `16372134` 
* `latitude`: e.g. `48208546`

Coordinate format: 16.372134° (degrees with 6 decimal places) * 1000000 => `16372134`

## Example

### Request URL

```HTTP
https://tickets.oebb.at/api/hafas/v1/stations?name=Wien
```

### Response Body

```json
[
    {
        "number": 1190100,
        "longitude": 16372134,
        "latitude": 48208547,
        "name": "",
        "meta": "Wien"
    }
]
```

`number` needs to be used for 