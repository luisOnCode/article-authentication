# Workflow

**| Three Entities |**
- Client
- Server
- Database


**| Client |**
 
_sends a POST request to an endpoint, specificating Username/Password_

**| Server |**

_needs to perform some validation_
    
- check on Database for if exists a valid user
- compare hashed passwords
- if accepted, generate a jwt access token and refresh token

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