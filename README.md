# passport-yahoo-oauth2-with-openid

This is a fork to get this published to NPM. It is not clear why the upstream has not
published this package to NPM however with the recent Yahoo changes it is no doubt
needed by more than just me so. Issue for lack of publishing opened here:

https://github.com/auth0/passport-yahoo-oauth2/issues/4


# Passport-Yahoo-OAuth

[Passport](http://passportjs.org/) strategies for authenticating with [Yahoo!](http://www.yahoo.com/)
using the OAuth 2 API.

This module lets you authenticate using Yahoo! in your Node.js applications.
By plugging into Passport, Yahoo! authentication can be easily and
unobtrusively integrated into any application or framework that supports
[Connect](http://www.senchalabs.org/connect/)-style middleware, including
[Express](http://expressjs.com/).

## Usage

#### Configure Strategy

The Yahoo authentication strategy authenticates users using a Yahoo account
and OAuth tokens.  The strategy requires a `verify` callback, which accepts
these credentials and calls `done` providing a user, as well as `options`
specifying a consumer key, consumer secret, and callback URL.

    passport.use(new YahooStrategy({
        clientID: YAHOO_CLIENT_ID,
        clientSecret: YAHOO_CLIENT_SECRET,
        callbackURL: "http://127.0.0.1:3000/auth/yahoo/callback"
      },
      function(token, tokenSecret, profile, done) {
        User.findOrCreate({ yahooId: profile.id }, function (err, user) {
          return done(err, user);
        });
      }
    ));

#### Authenticate Requests

Use `passport.authenticate()`, specifying the `'yahoo'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

    app.get('/auth/yahoo',
      passport.authenticate('yahoo'));

    app.get('/auth/yahoo/callback',
      passport.authenticate('yahoo', { failureRedirect: '/login' }),
      function(req, res) {
        // Successful authentication, redirect home.
        res.redirect('/');
      });

## Issues

If you receive a `401 Unauthorized` error, it is most likely because you have
not yet specified any application "Permissions".  Once you do so, Yahoo! will
generate new credentials for usage, and will then authenticate your requests
properly.

## Tests

    $ npm install --dev
    $ make test


## Credits

  - [Jared Hanson](http://github.com/jaredhanson)

## License

[The MIT License](http://opensource.org/licenses/MIT)

Copyright (c) 2012-2013 Jared Hanson <[http://jaredhanson.net/](http://jaredhanson.net/)>

<a target='_blank' rel='nofollow' href='https://app.codesponsor.io/link/vK9dyjRnnWsMzzJTQ57fRJpH/jaredhanson/passport-yahoo-oauth'>  <img alt='Sponsor' width='888' height='68' src='https://app.codesponsor.io/embed/vK9dyjRnnWsMzzJTQ57fRJpH/jaredhanson/passport-yahoo-oauth.svg' /></a>
