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