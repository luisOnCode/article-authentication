# Workflow

**| Three Entities |**
- Client
- Server
- Database


**| Client |**
 
_sends a POST request to an endpoint, specificating Username/Password_

**| Server |**

_needs to perform some validation_
    
- check on Database if exists a valid user
- compare hashed passwords
- if accepted, generate a jwt access token and refresh token

```
Hash x Cryptography

"Hashing" transforms data into something new. No algorithm can get the original value
"Encrypting" traffics data in a secure way. There's an algorithm at the end to redeem original value
```

```
Two types of JWT

    Access Token
        - used for accessing secured resources (routes)
        - short lived (15min to 1h)
        - vulnerable
    
    Refresh Token
        - used for new access token generation
        - longer lived (days or weeks)
        - more secure because of less traffic
        - security mechanisms
            . HTTP-only cookie (samesite)
            . Refresh Token Rotation
            . Refresh Token Automatic Reuse Detection
```
_server returns a 200 OK with Access Token + Refresh Token_


**| Client |**

```
Browser Threats

    - CSRF  (Cross Site Request Forgery)
        . Impersonating attempt through malicious URL
    
    - XSS   (Cross Site Scripting)
        . JavaScript Injection attempt through URL
```

```
Three ways of token storaging

    - Local Storage: Accessible with JavaScript, estimulating XSS threat
    - Memory: Demands constant requests to backend for new Refresh Tokens
    - Cookies: HTTP-only, Rotation, Reuse Detection and SameSite as security mechanisms
```

_client storages Access Token and Refresh Token on Cookies_

_client sends GET request to /protected-resource with Access Token_


**| Server |**

_middleware for token validation_
- signature
- expiration date
- custom claims

_server returns a 200 OK with Payload_



## Validation

**| Client |**

_client sends GET request to /protected-resource with Access Token_


**| Server |**

_server returns a 401 Error with Access Token expired_


**| Client |**

_instead of performing "Login Again" to get new access token, try "Refreshing Request"_

_client stores 401 on a queue_

_client sends POST request to /auth/refresh with RefreshToken=abc123_


**| Server |**

_server updates Access Token_

_server updates Refresh Token_

_server returns a 200 OK_


**| Client |**

_client sends GET request to /protected-resource with Access Token_


**| Server |**

_middleware for token validation_
- signature
- expiration date
- custom claims

_server returns a 200 OK with Payload_