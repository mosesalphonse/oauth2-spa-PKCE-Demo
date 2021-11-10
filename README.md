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


## Setup User accounts

You may create new Users, or you may link other user directory like AD, etc. For this example, I have created users within Auth0's database.

![image](https://user-images.githubusercontent.com/16347988/141109267-29a4abf4-9bdb-49c3-abf7-bb27caa23512.png)

## Build and Run the Single Page Application

Note: my code is modified a bit, make sure you use the code you downloaded.
~~~
git clone https://github.com/mosesalphonse/oauth2-spa-PKCE-Demo.git

cd oauth2-spa-PKCE-Demo
~~~
~~~
npm install && npm start
~~~

## Verification

Home Page

![image](https://user-images.githubusercontent.com/16347988/141111122-c8fe1fcc-c758-406c-a99c-7ee2422e5e41.png)

### After Clicking Login Button

a) Invoking 'authorize' endpoint with 'code_challenge', refer the below screenshot.


![image](https://user-images.githubusercontent.com/16347988/141112065-7ba94a6b-e016-47e4-9d31-c5b9bf2edcfd.png)

Note: 'code_challenge' is nothing but, a random text's hash value using 'code_challenge_method'

Here in this example, the code_challenge value is 'mAoSi0NclnylUPyf8KyVRsf0L4NZXGjzra2SrVizipw'. This hashed value will be stored in Authorization server(auth0) for future verification for this Client. This value should match with Code verification's hash value which we will pass later to authorization server(auth0). This verification step will be done by auth0, in this case.

b) After successful Login

![image](https://user-images.githubusercontent.com/16347988/141112942-bef851f6-8cab-41f0-bcfc-03af9b9513b8.png)

b) While getting Access Token

![image](https://user-images.githubusercontent.com/16347988/141113230-c2a1d82f-4bfe-4edd-999e-6d6983273de7.png)

Note: the code_verifier is 'VRH7Ncitq.dQE5baR6tOT.ld35TglhHv9Dj~ea~B9hX'

Use the below tool to hash the above code_verifier, the hashed value is 'mAoSi0NclnylUPyf8KyVRsf0L4NZXGjzra2SrVizipw', this value should match with Code_challenge which we initially passed while accessing 'authorize' endpoint. This step will be done by the authorization server(auth0)

https://tonyxu-io.github.io/pkce-generator/


