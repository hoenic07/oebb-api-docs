# GET /domain/v4/init

Authentication to generate an `accessToken`.

## URL

```HTTP
GET https://tickets.oebb.at/api/domain/v4/init
```

## Headers

``` HTTP
Channel: inet
```

## Example

### Response Body

```json
{
    "accessToken": "<your access token>",
    "token": {
        "accessToken": "<the same access token again>",
        "refreshToken": "<your refresh token>"
    },
    "channel": "inet",
    "supportId": "339e25c9",
    "cashId": "03",
    "orgUnit": 9525,
    "legacyUserMigrated": false,
    "userId": "anonym-a2907114-febf-46",
    "personId": "anonym-a2907114-febf-46",
    "customerId": "anonym-a2907114-febf-46",
    "realm": "customer",
    "sessionId": "...",
    "sessionTimeout": 2400,
    "sessionVersion": "0.0.2",
    "sessionCreatedAt": "2019-01-05T18:38:16.069Z",
    "xffxIP": "..."
}
```