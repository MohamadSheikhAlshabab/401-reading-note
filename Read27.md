#Readings: Authentication & Production Server [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read27.md)

##  Introduction to JSON Web Tokens

  - __What is JSON Web Token?__
    - JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.
    - This information can be verified and trusted because it is digitally signed.
    - JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA. 
  
  - __When should you use JSON Web Tokens?__
  
    - __Authorization:__ This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token
    - __Information Exchange:__ JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. 
  
  - __What is the JSON Web Token structure?__
    - SON Web Tokens consist of three parts separated by dots (.), which are:
        - __Header__: consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.
        - __Payload__: contains the claims. Claims are statements about an entity (typically, the user) and additional data. three types of claims: registered, public, and private claims.
        - __Signature__: To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.
    -  a JWT typically looks like: xxxxx.yyyyy.zzzzz
    
  - __Why should we use JSON Web Tokens?__
    - As JSON is less verbose than XML, when it is encoded its size is also smaller, making JWT more compact than SAML. This makes JWT a good choice to be passed in HTML and HTTP environments.
    - JSON parsers are common in most programming languages because they map directly to objects. Conversely, XML doesn't have a natural document-to-object mapping. This makes it easier to work with JWT than SAML assertions.

---

## How to Use JWT Authentication with Django REST Framework
  - JWT stand for JSON Web Token and it is an authentication strategy used by client/server applications where the client is a Web application using JavaScript and some frontend framework like Angular, React or VueJS.
  - __How JWT Works?__
    - `curl http://127.0.0.1:8000/hello/ -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQzODI4NDMxLCJqdGkiOiI3ZjU5OTdiNzE1MGQ0NjU3OWRjMmI0OTE2NzA5N2U3YiIsInVzZXJfaWQiOjF9.Ju70kdcaHKn1Qaz8H42zrOYk0Jx9kIckTn9Xx7vhikY'`
    - The JWT is acquired by exchanging an username + password for an access token and an refresh token.
    - The access token is usually short-lived (expires in 5 min or so, can be customized though).
    - The refresh token lives a little bit longer (expires in 24 hours, also customizable). 
    - It is comparable to an authentication session. After it expires, you need a full login with username + password again.
    
    - ```
    
        header = eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9
        payload = eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQzODI4NDMxLCJqdGkiOiI3ZjU5OTdiNzE1MGQ0NjU3OWRjMmI0OTE2NzA5N2U3YiIsInVzZXJfaWQiOjF9
        signature = Ju70kdcaHKn1Qaz8H42zrOYk0Jx9kIckTn9Xx7vhikY
        
      ```
    - header

                {
                  "typ": "JWT",
                  "alg": "HS256"
                }
                
    - payload

              {
                "token_type": "access",
                "exp": 1543828431,
                "jti": "7f5997b7150d46579dc2b49167097e7b",
                "user_id": 1
              }
              
     - signature: 
        - The signature is issued by the JWT backend, using the header base64 + payload base64 + SECRET_KEY.
        - Upon each request this signature is verified.
        - If any information in the header or in the payload was changed by the client it will invalidate the signature.
        - The only way of checking and validating the signature is by using your application’s SECRET_KEY.
        - Among other things, that’s why you should always keep your SECRET_KEY secret!
        
        
---
- __Installation & Setup__:
  - `pip install djangorestframework_simplejwt`
  - settings.py

                  REST_FRAMEWORK = {
                      'DEFAULT_AUTHENTICATION_CLASSES': [
                          'rest_framework_simplejwt.authentication.JWTAuthentication',
                      ],
                  }

   -  urls.py

                  from django.urls import path
                  from rest_framework_simplejwt import views as jwt_views

                  urlpatterns = [
                      # Your URLs...
                      path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
                      path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
                  ]

---
- __Obtain Token__:
  - First step is to authenticate and obtain the token. The endpoint is /api/token/ and it only accepts POST requests.`http post http://127.0.0.1:8000/api/token/ username=vitor password=123`
  - ![img](https://simpleisbetterthancomplex.com/media/2018/12/jwt-obtain-token.png)
  - your response body is the two tokens:
               ```         {
                      "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQ1MjI0MjU5LCJqdGkiOiIyYmQ1NjI3MmIzYjI0YjNmOGI1MjJlNThjMzdjMTdlMSIsInVzZXJfaWQiOjF9.D92tTuVi_YcNkJtiLGHtcn6tBcxLCBxz9FKD3qzhUg8",
                      "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTU0NTMxMDM1OSwianRpIjoiMjk2ZDc1ZDA3Nzc2NDE0ZjkxYjhiOTY4MzI4NGRmOTUiLCJ1c2VyX2lkIjoxfQ.rA-mnGRg71NEW_ga0sJoaMODS5ABjE5HnxJDb0F8xAo"
                      }
               ``` 
   - to access the protected views on the backend, you should include the access token in the header of all requests, like this:`http http://127.0.0.1:8000/hello/ "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBl`

- __Refresh Token__
  - To get a new access token, you should use the refresh token endpoint /api/token/refresh/ posting the refresh token:`http post http://127.0.0.1:8000/api/token/refresh/ refresh=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTU0NTMwODIyMiwianRpIjoiNzAyOGFlNjc0ZTdjNDZlMDlmMzUwYjg3MjU1NGUxODQiLCJ1c2VyX2lkIjoxfQ.Md8AO3dDrQBvWYWeZsd_A1J39z6b6HEwWIUZ7ilOiPE`
