# oauth2-spa-PKCE-Demo
Single Page Application and its Security with Oauth2 Authorization Code Flow with Proof Key for Code Exchange (PKCE)

## Background
In Single Page App or Mobile App, we use Oauth 2.0's authorization code grant type for security. In Authorization code grant type,  first call (authorization request) is made through a browser or User-Agent to obtain the authorization code. This makes the auth code vulnerable to an “Authorization Code Interception Attack”. In simple terms, there is a chance someone could steal that auth code.

And Also Front Channel(SPA) is not safe to store any credentals like client secret, So they use Implicit Flow.

For native and browser-based JavaScript apps, it is now widely considered a best practice to use the Authorization Code flow with the PKCE extension, instead of the Implicit flow.

This flow is like the regular Authorization Code flow, except PKCE replaces the client secret used in the standard Authorization Code flow with a one-time code challenge. This means the client app doesn’t have to store a client secret.
