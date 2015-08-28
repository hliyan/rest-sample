# rest-sample
A simple, practical (warning: but NOT fully compliant) RESTful API sample.

# headers

## request headers

- all requests (except login) should send auth token

```
Authorization: token <token received in login response>
```

## response headers

- all responses should contain JSON

```
Content-Type: application/json; charset=utf-8
```

# API

## login

#### login request
```
POST /login
{
  "username": "john",
  "password": "1234"
}
```

#### login response - success
```
201 Created
{
  "token": "12345678"
}
```

#### login response - auth fail
```
404 Not Found
{
  "message": "The credentials you entered are not recognized"
}
```

# users

## create user

#### create user request

```
POST /users
{
  "username": "joe",
  "password": "123456"
}
```

#### create user response - success

```
201 OK
{
  "uid": "2",
  "username": "joe",
  "group": { "uid": "1", "name": "Default" }
}
```
- responses set server generated values and defaults
- does not send secret fields
- embeds at a minimum the uid (and usually a name) for foreign key constraints

#### create user response - fail - validations

```
400 Bad Request
{
  "message": "Validation failed",
  "fields": {
    "username": "Username should be at least 5 characters in length.",
    "password": "Password is required."
  }
}
```

## list users

#### list users request

```
GET /users
```

#### list users response

```
200 OK
{
  "data": [
    { "uid": "1", "username": "john", "group": { "uid": "1", "name": "Default Group" } },
    { "uid": "2", "username": "joe", "group": { "uid": "1", "name": "Default Group" } }
  ]
}
```

## get user details

#### user detail request

```
GET /users/2
```

#### user detail response

```
201 OK
{
  "uid": "2",
  "username": "joe",
  "group": { "uid": "1", "name": "Default" }
}
```

## update user

#### update user request

```
PUT /users/2
{
  "username": "joe",
  "password": "123456",
  "group": { "uid": "2"}
}
```

#### update user response - success

```
200 OK
{
  "uid": "2",
  "username": "joe",
  "group": { "uid": "2", "name": "Administrators" }
}
```

## delete user

#### delete user request

```
DELETE /users/2
```

#### delete user response - success

```
200 OK
{
  "uid": "2",
  "username": "joe",
  "group": { "uid": "2", "name": "Administrators" }
}
```
- delete response sends the last state of the record before it was deleted

# standard error responses
- 200 OK - Request succeeded. Response included
- 201 Created - Resource created. URL to new resource in Location header
- 204 No Content - Request succeeded, but no response body
- 400 Bad Request - Could not parse request
- 401 Unauthorized - No authentication credentials provided or authentication failed
- 403 Forbidden - Authenticated user does not have access
- 404 Not Found - Resource not found
- 500, 501, 502, 503, etc - An internal server error occured

# summary data
- TODO

# embedded data
- TODO
