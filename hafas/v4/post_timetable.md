# POST /hafas/v4/timetable

Get connections between two stations.

## URL

```HTTP
POST https://tickets.oebb.at/api/hafas/v4/timetable
```

## Headers

``` HTTP
AccessToken: <your access token>
x-ts-supportid: 1
Content-Type: application/json
Channel: inet
```

Use the [Authentication endpoint](../../domain/v4/get_init.md) to generate the access token.

## Body

```json
{
    "datetimeDeparture": "2019-01-06T18:40:00.000", // Time of departure. xor with datetimeArrival
    "datetimeArrival":"2019-01-06T18:40:00.000", // Time of arrival. xor with datetimeDeparture
    "filter": { // All values default to false
        "regionaltrains": false, // true: Only connections with regional trains
        "direct": false, // true: Only direct connections (= no train changes)
        "changeTime": false, // default change time (false) or minumum time for changing a train in minutes (0-20)
        "wheelchair": false, // true: Only show accessibly designed connections
        "bikes": false, // true: Only show connections that support transporting bikes.
        "trains": false, // true: Only show train connections (= no buses etc.)
    },
    "passengers": [ // Array requires a value for a successful response 
        {}
    ],
    "count": 5, // No. of returned connections. Default: 5. Maximum: 6
    "from": {
        "number": 1161226 // Start Station Number
    },
    "to": {
        "number": 1161108 // Destination Station Number
    }
}
```
The `number` values for `from` and `to` needs to be used from the [Stations](../v1/get_stations.md) response.

Only options available on https://tickets.oebb.at are documented.

## Example

### Request Body

```json
{
    "datetimeDeparture": "2019-01-05T16:28:55.597",
    "passengers": [
        {}
    ],
    "count": 1,
    "from": {
        "number": 1161226
    },
    "to": {
        "number": 1161108
    }
}
```

### Response Body

```json
{
    "connections": [
        {
            "id": "baba91ff6cb40ffffd7731b9ff3ac71f641c74d0725230124c6c9dc9606082c4",
            "from": {
                "name": "Bad Mitterndorf Bahnhof",
                "esn": 8100165,
                "departure": "2019-01-05T17:59:00.000",
                "departurePlatform": "2",
                "showAsResolvedMetaStation": true
            },
            "to": {
                "name": "Leoben Hbf",
                "esn": 8100070,
                "arrival": "2019-01-05T19:29:00.000",
                "arrivalPlatform": "2",
                "showAsResolvedMetaStation": true
            },
            "sections": [
                {
                    "from": {
                        "name": "Bad Mitterndorf Bahnhof",
                        "esn": 8100165,
                        "departure": "2019-01-05T17:59:00.000",
                        "departurePlatform": "2"
                    },
                    "to": {
                        "name": "Stainach-Irdning Bahnhof",
                        "esn": 8100132,
                        "arrival": "2019-01-05T18:15:00.000",
                        "arrivalPlatform": "2"
                    },
                    "duration": 960000,
                    "category": {
                        "name": "REX",
                        "number": "4414",
                        "shortName": "REX",
                        "displayName": "REX",
                        "longName": {
                            "de": "Regional Express",
                            "en": "Regional Express",
                            "it": "Regional-Express"
                        },
                        "backgroundColor": "#ffffff",
                        "fontColor": "#D40027",
                        "barColor": "#D40027",
                        "place": {
                            "de": "Bahnsteig",
                            "en": "Platform",
                            "it": "Binaro"
                        },
                        "journeyPreviewIconId": "zug-disabled",
                        "journeyPreviewIconColor": "#878787",
                        "assistantIconId": "zugAssistant",
                        "train": true,
                        "parallelLongName": "RegionalExpress",
                        "parallelDisplayName": "REX",
                        "backgroundColorDisabledMobile": "#00F0F0F0",
                        "backgroundColorDisabled": "#F0F0F0",
                        "fontColorDisabled": "#878787",
                        "barColorDisabled": "#878787"
                    },
                    "type": "journey",
                    "hasRealtime": false
                },
                {
                    "from": {
                        "name": "Stainach-Irdning Bahnhof",
                        "esn": 8100132,
                        "departure": "2019-01-05T18:21:00.000",
                        "departurePlatform": "3"
                    },
                    "to": {
                        "name": "Leoben Hbf",
                        "esn": 8100070,
                        "arrival": "2019-01-05T19:29:00.000",
                        "arrivalPlatform": "2"
                    },
                    "duration": 4080000,
                    "category": {
                        "name": "IC",
                        "number": "611",
                        "shortName": "IC",
                        "displayName": "IC",
                        "longName": {
                            "de": "Intercity",
                            "en": "Intercity",
                            "it": "Intercity"
                        },
                        "backgroundColor": "#ffffff",
                        "fontColor": "#afafaf",
                        "barColor": "#e2002a",
                        "place": {
                            "de": "Bahnsteig",
                            "en": "Platform",
                            "it": "Binaro"
                        },
                        "journeyPreviewIconId": "zug-disabled",
                        "journeyPreviewIconColor": "#878787",
                        "assistantIconId": "zugAssistant",
                        "train": true,
                        "parallelLongName": "RegionalExpress",
                        "parallelDisplayName": "REX",
                        "backgroundColorDisabledMobile": "#00F0F0F0",
                        "backgroundColorDisabled": "#F0F0F0",
                        "fontColorDisabled": "#878787",
                        "barColorDisabled": "#878787"
                    },
                    "type": "journey",
                    "hasRealtime": false
                }
            ],
            "switches": 1,
            "duration": 5400000,
            "pastConnection": true
        }
    ]
}
```