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
