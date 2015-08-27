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
  "uid": "4ac34i",
  "username": "joe",
  "group": { "uid": "21", "name": "Default" }
}
```
- responses set server generated values and defaults
- does not send secret fields
- embeds at a minimum the uid (and usually a name) for foreign key constraints
