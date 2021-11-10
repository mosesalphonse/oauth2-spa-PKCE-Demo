# oauth2-spa-PKCE-Demo
Single Page Application and its Security with Oauth2 Authorization Code Flow with Proof Key for Code Exchange (PKCE)

## Background
In Single Page App or Mobile App, we use Oauth 2.0's authorization code grant type for security. In Authorization code grant type,  first call (authorization request) is made through a browser or User-Agent to obtain the authorization code. This makes the auth code vulnerable to an “Authorization Code Interception Attack”. In simple terms, there is a chance someone could steal that auth code.

And Also Front Channel(SPA) is not safe to store any credentals like client secret, So they use Implicit Flow.

For native and browser-based JavaScript apps, it is now widely considered a best practice to use the Authorization Code flow with the PKCE extension, instead of the Implicit flow.

This flow is like the regular Authorization Code flow, except PKCE replaces the client secret used in the standard Authorization Code flow with a one-time code challenge. This means the client app doesn’t have to store a client secret.

## Authorization Server, Client App cinfig (used Auth0)

Step 1: Setup your Auth0 tenancy and login into that

Step 2: Create Single Page Application client as shown in the below screenshot

![image](https://user-images.githubusercontent.com/16347988/141107689-b4f55820-0d7d-4c65-b350-07add79c0303.png)


Step 3: Go to the new created Single Page Application under 'settings' and configure your Callback URL, Logout URL and Allowed Web origins as shown in the below screenshot

![image](https://user-images.githubusercontent.com/16347988/141108374-0ce78ef4-15d1-4b2b-8cc1-cadca68a79f6.png)

Step 4: Download the sample JavaScript Code, can be found under 'Quick start' as shown in the screenshot

![image](https://user-images.githubusercontent.com/16347988/141108760-0a619664-7452-4c1f-a92f-4712bcf7979f.png)

