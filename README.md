# rest-sample
A simple, practical (warning: but NOT fully compliant) RESTful API sample.

## login

#### request
```
POST /login
{
  "username": "john",
  "password": "1234"
}
```

#### response - success
```
201 OK
{
  "token": "12345678"
}
```
