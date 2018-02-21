# OneLogin OpenId Connect Implicit Flow Sample

The sample is an [Express.js](https://expressjs.com/) app that uses
[Passport.js](http://www.passportjs.org/) and the [Passport-OpenIdConnect](https://github.com/jaredhanson/passport-openidconnect)
module for managing user authentication.

The sample tries to keep everything as simple as possible so only
implements
* Login - redirecting users to OneLogin for authentication
* Logout - destroying the local session and revoking the token at OneLogin
* User Info - fetching profile information from OneLogin

## Setup
In order to run this sample you need to setup an OpenId Connect
app in your OneLogin Admin portal.

If you don't have a OneLogin developer account [you can sign up here](https://www.onelogin.com/developer-signup).

1. Clone this repo
2. Rename `.env.sample` to `.env` and update the **client_id** and
**client_secret** you obtained from OneLogin as well as the **subdomain**
of your OneLogin account and the Redirect Uri of your local site.

You need to make sure that this matches what you specified as the
Redirect Uri when you setup your OIDC app connector in the OneLogin portal.

## Run
This sample uses an express app running on nodejs.

From the command line run
```
> npm install
> npm start
```

### Local testing
By default these samples will run on `http://localhost:3000` but since localhost
is not supported by the OIDC spec you will need to use a tool like [Ngrok](https://ngrok.com/)
for local testing.

Install ngrok using `npm install -g ngrok` then run `ngrok http 3000` and Ngrok will
give you a public HTTPS url that you can browse to and see your local app.

You will need to set this Ngrok url as the **redirect_uri** in your OneLogin OIDC app
via the Admin portal and also in your `.env` file.