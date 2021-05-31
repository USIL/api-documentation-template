# Create User's Account

Create an Account for the authenticated User if an Account for that User does
not already exist. Each User can only have one Account.

**Base Url** : `http://acme.com`

**Endpoint** : `/api/accounts/`

**Method** : `POST`

**Auth required** : YES

| header key | header value | description |
|------------|--------------|-------------|
| Authorization  | Bearer AKfycbyF7II | security token with 3600 ml of duration|

**Permissions required** : None

## Request

```json
{
    "name": "Jane",
    "lastname": "Doe",
    "cod_tr_acme": "787-aeq11"
}
```

**Request Description**

| key | value | description |
|------------|--------------|-------------|
| name  |  Jane | user name |
| lastname  |  Doe | user lastname |
| cod_tr_acme  |  787-aeq11 | user code in acme system |

**Request Headers**

| header key | header value | description |
|------------|--------------|-------------|
| x-usil-request-id  |  4512451 | random alphanumeric value which identify this event |
| x-usil-consumer-id | loney_tones_server | string value which identifies who is consuming this endpoint |
|            |              |             |


## Response

```json
{
    "code": 200000,
    "message": "success",
    "content": {
      "id": 123
    }
}
```

**Response Description**


| key | value | description |
|------------|--------------|-------------|
| id  |  123 | id of created person  |

**Response Headers**

| header key | header value | description |
|------------|--------------|-------------|
| x-usil-request-id  |  4512451 | random alphanumeric value which identify this event |


- If response is success, http status will be **200**
- If response has an error in backend, http status will be the standard: 401, 403, 500, 502, etc
- Related to the http status, will be a code in http body:
  - 400xyz
  - 500xyz
  - 600xyz

**Response error codes**

```json
{
    "code": 500403,
    "message": "permission denied"
}
```

| code | description |
|------------|-------------|
| 500403  | user or client is not allowed to execute this endpoint  |
