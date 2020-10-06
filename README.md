# Spring Boot 2 Login Samples

[![CircleCI](https://circleci.com/gh/auth0-samples/auth0-spring-boot-login-samples.svg?style=svg)](https://circleci.com/gh/auth0-samples/auth0-spring-boot-login-samples)

https://circleci.com/gh/auth0-samples/auth0-spring-boot-login-samples.svg?style=svg

This repository contains samples demonstrating how to add authentication with Auth0 to your Spring Boot application.

- [MVC/Servlet sample](./mvc-login)
- [WebFlux sample](./webflux-login)

## What is Auth0?

Auth0 helps you to:

* Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter, Box, Salesforce, amont others**, or enterprise identity systems like **Windows Azure AD, Google Apps, Active Directory, ADFS or any SAML Identity Provider**.
* Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
* Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
* Support for generating signed [Json Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
* Analytics of how, when and where users are logging in.
* Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).

## Create a free Auth0 account

1. Go to [Auth0](https://auth0.com/signup) and click Sign Up.
2. Use Google, GitHub or Microsoft Account to login.

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## Author

[Auth0](https://auth0.com)

## License

This project is licensed under the MIT license. See the [LICENSE](LICENSE) file for more info.


## Steve::API access:
** jwks(web token keys):
https://pnpinfos.auth0.com/.well-known/jwks.json

** configured a machin to machine app in auth0.

** get access token from auth0:
curl --request POST \
  --url https://pnpinfos.auth0.com/oauth/token \
  --header 'content-type: application/json' \
  --data '{"client_id":"Yv8ag5pKdScgQwTZ5eC7EArHWdKQ2J5k","client_secret":"bTvFM5XXujxAG3m9FvCNMYrI5ZFv24TJdq2lJze_SYNVvPF7rURsfL-YhzU6M5I9","audience":"https://appointments","grant_type":"client_credentials"}' | jq

** access api at http://localhost:4000/authorized
curl --request GET \
  --url http://localhost:4000/authorized \
  --header 'authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6Ik9UUkdSakk0TkVJeE4wVkZPVUpGTWtKQ056Y3dSak15UWtVMVFVWkNNa1V4TkVKR01qWXlNQSJ9.eyJpc3MiOiJodHRwczovL3BucGluZm9zLmF1dGgwLmNvbS8iLCJzdWIiOiJZdjhhZzVwS2RTY2dRd1RaNWVDN0VBckhXZEtRMko1a0BjbGllbnRzIiwiYXVkIjoiaHR0cHM6Ly9hcHBvaW50bWVudHMiLCJpYXQiOjE2MDE0MDY0NDQsImV4cCI6MTYwMTQ5Mjg0NCwiYXpwIjoiWXY4YWc1cEtkU2NnUXdUWjVlQzdFQXJIV2RLUTJKNWsiLCJndHkiOiJjbGllbnQtY3JlZGVudGlhbHMifQ.c8JCioFF84uGpI-07C-vPWJRuspX-msZKmbr5aDNi7tiZyPpWXkH-9aKO4okfz3nmfIxSV2NqGkmSc0xZZeZQ6CE-vBM84W3HaJ3F-YCohEjqlJSp3KnF4S1T1x2gZwUrrrpSiggopHo-VYRbe4mw5iNbvgsckU8pTnfAK_aXvfgtMzBVHwtzNn670BviwWXde9X1bU-CN9PO38fCxUqTUfkNsVjPqo56sFZMnvzXi3-9fbGksGcMk7Z5rjZVLgkKDXjqk2eTCdKG_5Qhsm3M5d9N0i6vlDdCi6LiVRvJz2wwaj8_-I2FeAsXpXfHvnM2kHvKHgE-sgVnxyyzmk6AA'

  ** install npm packages:
npm install express
npm install express-jwt
npm install jwks-rsa

** host your api:
node myapi.js

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
var express = require('express');
var app = express();
var jwt = require('express-jwt');
var jwks = require('jwks-rsa');

var port = process.env.PORT || 4000;

var jwtCheck = jwt({
      secret: jwks.expressJwtSecret({
          cache: true,
          rateLimit: true,
          jwksRequestsPerMinute: 5,
          jwksUri: 'https://pnpinfos.auth0.com/.well-known/jwks.json'
    }),
    audience: 'https://appointments',
    issuer: 'https://pnpinfos.auth0.com/',
    algorithms: ['RS256']
});

app.use(jwtCheck);

app.get('/authorized', function (req, res) {
    res.send('Secured Resource');
});

app.listen(port);
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>.