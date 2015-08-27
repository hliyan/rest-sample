# rest-sample
A simple, practical (warning: but NOT fully compliant) RESTful API sample.

# headers
- TODO

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
201 Created
{
  "token": "12345678"
}
```

#### response - auth fail
```
404 Not Found
{
  "message": "The credentials you entered are not recognized"
}
```
