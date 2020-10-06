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
  --data '{"client_id":"","client_secret":"","audience":"https://appointments","grant_type":"client_credentials"}' | jq

** access api at http://localhost:4000/authorized
curl --request GET \
  --url http://localhost:4000/authorized \
  --header 'authorization: Bearer eyJhbGciOiJSUzIdfgdgdfg435325325yyzmk6AA'

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