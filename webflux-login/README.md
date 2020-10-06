# Spring Boot 2 Login - WebFlux

This sample demonstrates:

- Adding authentication with Auth0 to a Spring Boot 2 WebFlux application
- Accessing profile information of the authenticated user
- Only allowing authenticated users to access certain resources

## Configuration

### Auth0 Dashboard
1. On the [Auth0 Dashboard](https://manage.auth0.com/#/clients) create a new Application of type **Regular Web Application**.
1. On the **Settings** tab of your application, add the URL `http://localhost:3000/login/oauth2/code/auth0` to the **Allowed Callback URLs** field.
1. On the **Settings** tab of your application, add the URL `http://localhost:3000/` to the **Allowed Logout URLs** field.
1. Save the changes to your application settings. Don't close this page; you'll need some of the settings when configuring the application below.

### Application configuration

Copy `src/main/resources/application.yml.example` to `src/main/resources/application.yml`:

```bash
cp src/main/resources/application.yml.example src/main/resources/application.yml
```

Set the application values in the `src/main/resources/application.yml` file to the values of your Auth0 application.

```yaml
client-id: {YOUR-CLIENT-ID}
client-secret: {YOUR-CLIENT-SECRET}
issuer-uri: https://{YOUR-DOMAIN}/
```

### Running the sample

Open a terminal, go to the project root directory and run the following command:

Linux or MacOS:

```bash
./gradlew bootRun
```

Windows:

```bash
gradlew.bat bootRun 
```

The application will be accessible at http://localhost:3000.

### Running the sample with docker

In order to run the example with [Docker](https://docs.docker.com/install/) you need to have `docker` installed.

You also need to set the client values as explained [previously](#application-configuration).

Execute the command to run Docker for your environment:

Linux or MacOS:

```bash
sh exec.sh
```

Windows:

```bash
.\exec.ps1
```

The application will be accessible at http://localhost:3000.

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## What is Auth0?

Auth0 helps you to:

* Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter, Box, Salesforce, amont others**, or enterprise identity systems like **Windows Azure AD, Google Apps, Active Directory, ADFS or any SAML Identity Provider**.
* Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
* Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
* Support for generating signed [Json Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
* Analytics of how, when and where users are logging in.
* Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).

## Create a free account in Auth0

1. Go to [Auth0](https://auth0.com) and click Sign Up.
2. Use Google, GitHub or Microsoft Account to login.

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## Author

[Auth0](https://auth0.com)

## License

This project is licensed under the MIT license. See the [LICENSE](../LICENSE) file for more info.

## Steve::flows:
localhost:3000
-->
https://pnpinfos.auth0.com/login?state=g6Fo2SBPU0U5c2ZXSUtRZlFQSXM5VnFXVTlPODF3cjdfS3FOQ6N0aWTZIG9pdkZYTXdFTmt6OG1DODhqVDFhdlJuRGFYVEg4S2pwo2NpZNkgbzBpN01ncm4wMnNHeXhieEJEaDdJN29mN1FTSzZYWGQ&client=o0i7Mgrn02sGyxbxBDh7I7of7QSK6XXd&protocol=oauth2&response_type=code&scope=openid%20profile%20email&redirect_uri=http%3A%2F%2Flocalhost%3A3000%2Flogin%2Foauth2%2Fcode%2Fauth0&nonce=2II-z94LsiwAS3-8_Q-JB_DgHfKPAeFkRLoRrUk--Ig

-->
https://accounts.google.com/o/oauth2/auth/oauthchooseaccount?response_type=code&redirect_uri=https%3A%2F%2Flogin.auth0.com%2Flogin%2Fcallback&scope=email%20profile&state=viodzyti7gbfwxWvVB2hhjUZ8seFbXfY&client_id=104565000066-q7q63bouq2ct8gj73drmpu186amn6a3f.apps.googleusercontent.com&flowName=GeneralOAuthFlow

-->
https://login.auth0.com/decision?state=g6Fo2SBXcTVZVExtTDNqOUswbjY1UHA0Y2RBSV92UHJ5ZXd3bKN0aWTZIG9RMDgyam10RjNuc0NPbk9LbXlXNUI1ZTlhY3kzVERHo2NpZNkgbzBpN01ncm4wMnNHeXhieEJEaDdJN29mN1FTSzZYWGQ#

-->
http://localhost:3000/

-----------------------------------------------------
http://localhost:3000/ 

-->
GET http://localhost:3000/oauth2/authorization/auth0
--> 302
https://pnpinfos.auth0.com/authorize?response_type=code&client_id=o0i7Mgrn02sGyxbxBDh7I7of7QSK6XXd&scope=openid%20profile%20email&state=nsE7dMgqP3V6HjmULCxicQ2Y-d8wZhIxYhh5SF2n9nc%3D&redirect_uri=http://localhost:3000/login/oauth2/code/auth0&nonce=2II-z94LsiwAS3-8_Q-JB_DgHfKPAeFkRLoRrUk--Ig
--> 302
GET /login?state=g6Fo2SBPU0U5c2ZXSUtRZlFQSXM5VnFXVTlPODF3cjdfS3FOQ6N0aWTZIG9pdkZYTXdFTmt6OG1DODhqVDFhdlJuRGFYVEg4S2pwo2NpZNkgbzBpN01ncm4wMnNHeXhieEJEaDdJN29mN1FTSzZYWGQ&client=o0i7Mgrn02sGyxbxBDh7I7of7QSK6XXd&protocol=oauth2&response_type=code&scope=openid%20profile%20email&redirect_uri=http%3A%2F%2Flocalhost%3A3000%2Flogin%2Foauth2%2Fcode%2Fauth0&nonce=2II-z94LsiwAS3-8_Q-JB_DgHfKPAeFkRLoRrUk--Ig
--> 200

POST https://pnpinfos.auth0.com/usernamepassword/challenge
Payload:
{"state":"g6Fo2SBPU0U5c2ZXSUtRZlFQSXM5VnFXVTlPODF3cjdfS3FOQ6N0aWTZIG9pdkZYTXdFTmt6OG1DODhqVDFhdlJuRGFYVEg4S2pwo2NpZNkgbzBpN01ncm4wMnNHeXhieEJEaDdJN29mN1FTSzZYWGQ"}

--> 200
GET https://pnpinfos.auth0.com/user/ssodata

--> 404
GET https://pnpinfos.auth0.com/authorize?client_id=o0i7Mgrn02sGyxbxBDh7I7of7QSK6XXd&response_type=code&redirect_uri=http%3A%2F%2Flocalhost%3A3000%2Flogin%2Foauth2%2Fcode%2Fauth0&scope=openid%20profile%20email&state=g6Fo2SBPU0U5c2ZXSUtRZlFQSXM5VnFXVTlPODF3cjdfS3FOQ6N0aWTZIG9pdkZYTXdFTmt6OG1DODhqVDFhdlJuRGFYVEg4S2pwo2NpZNkgbzBpN01ncm4wMnNHeXhieEJEaDdJN29mN1FTSzZYWGQ&nonce=2II-z94LsiwAS3-8_Q-JB_DgHfKPAeFkRLoRrUk--Ig&connection=google-oauth2&is_submitting=false&sso=true&protocol=oauth2&_csrf=HAKxI213-NR1qK3KjD20OUkOHJiPJMagbo40&_intstate=deprecated&auth0Client=eyJuYW1lIjoibG9jay5qcy11bHAiLCJ2ZXJzaW9uIjoiMTEuMjYuMyIsImVudiI6eyJhdXRoMC5qcy11bHAiOiI5LjEzLjQiLCJhdXRoMC5qcyI6IjkuMTMuNCJ9fQ%3D%3D
--> 302
https://login.auth0.com/pnpinfos/authorize?client_id=o0i7Mgrn02sGyxbxBDh7I7of7QSK6XXd&response_type=code&redirect_uri=http%3A%2F%2Flocalhost%3A3000%2Flogin%2Foauth2%2Fcode%2Fauth0&scope=openid%20profile%20email&state=nsE7dMgqP3V6HjmULCxicQ2Y-d8wZhIxYhh5SF2n9nc%3D&nonce=2II-z94LsiwAS3-8_Q-JB_DgHfKPAeFkRLoRrUk--Ig&connection=google-oauth2&is_submitting=false&sso=true&protocol=oauth2&_csrf=HAKxI213-NR1qK3KjD20OUkOHJiPJMagbo40&auth0Client=eyJuYW1lIjoibG9jay5qcy11bHAiLCJ2ZXJzaW9uIjoiMTEuMjYuMyIsImVudiI6eyJhdXRoMC5qcy11bHAiOiI5LjEzLjQiLCJhdXRoMC5qcyI6IjkuMTMuNCJ9fQ%3D%3D

--> 302
https://accounts.google.com/o/oauth2/auth?response_type=code&redirect_uri=https%3A%2F%2Flogin.auth0.com%2Flogin%2Fcallback&scope=email%20profile&state=viodzyti7gbfwxWvVB2hhjUZ8seFbXfY&client_id=104565000066-q7q63bouq2ct8gj73drmpu186amn6a3f.apps.googleusercontent.com

--> 200
POST https://accounts.google.com/_/signin/oauth?authuser=0&hl=en-GB&_reqid=178758&rt=j

--> 200
https://accounts.google.com/signin/oauth/consent?authuser=0&part=AJi8hAOrJojENy77lGfWKM1Z_U0NkP78wXLYzg2sPI8cz0en2FY4RyJJ6DtqHHE8I2dyXvy2CHl3abwnhd0zAp7lkeSMF2fNe2OoruZEnHI-EFSuqEUWYIBgT9Cp4_ue4hv5NnjyepLCzHJ22im8RtwUt4qpUvM1q6WR8ktkUv_u1aA5vVRKGm8J71vdbCOoM67GhmW9nNBo6dhKclStrIcXG01Fta_qRD0gIr58PtIhvjuyo3fYQecb1LPteFo5Mglu6hoXPhPCu2ORWO3ZmVmqSrkha-gvuHcN3Nl3z7MmQlzNAqf2fnlwPNlXDs1qROfko0OaDNPzfX9MM5VXZ6-olA5fpGfiY4iX2cmH13bZJejJ7xGOinU3TgnEnRevXwlYYa0_l6LMgYJjRxrk_OobCjZTaP9J5Sr5xF3JcGsa0_EFAxqan08HznYuIpTIdzn9GG6uhESc&as=S-1442482271%3A1601171501445063&pli=1&rapt=AEjHL4OmovrpPCvFXvh5RS92Glg0odOyJ0BMz_63XiMa10kcQJ8GMEm8ivmYAdgYxbFD1Sykf_fmiDhzD6MchhI7jlC__ZEVkQ

--> 302
https://login.auth0.com/login/callback?state=viodzyti7gbfwxWvVB2hhjUZ8seFbXfY&code=4%2F4gGyxNcpimc6Z_yjNSrJYXgK5yXe9w1tfpo-LKJCEieZ7rnLhkbkBgaOegeFETHpduPjeDzGwNVsgBEPG3owWtU&scope=email+profile+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.profile+openid&authuser=0&prompt=consent

--> 302
https://login.auth0.com/decision?state=g6Fo2SBXcTVZVExtTDNqOUswbjY1UHA0Y2RBSV92UHJ5ZXd3bKN0aWTZIG9RMDgyam10RjNuc0NPbk9LbXlXNUI1ZTlhY3kzVERHo2NpZNkgbzBpN01ncm4wMnNHeXhieEJEaDdJN29mN1FTSzZYWGQ

-->
POST https://login.auth0.com/decision
form data:
state=g6Fo2SBXcTVZVExtTDNqOUswbjY1UHA0Y2RBSV92UHJ5ZXd3bKN0aWTZIG9RMDgyam10RjNuc0NPbk9LbXlXNUI1ZTlhY3kzVERHo2NpZNkgbzBpN01ncm4wMnNHeXhieEJEaDdJN29mN1FTSzZYWGQ&audience=https%3A%2F%2Fpnpinfos.auth0.com%2Fuserinfo&scope%5B%5D=openid&scope%5B%5D=profile&scope%5B%5D=email

--> Authorization Code returned to redirect(callback) url:
http://localhost:3000/login/oauth2/code/auth0?code=6Tcwj8mX38x11Soq&state=nsE7dMgqP3V6HjmULCxicQ2Y-d8wZhIxYhh5SF2n9nc%3D

--> Back to page:
http://localhost:3000/




