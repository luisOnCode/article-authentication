# What do I have until now...

## OAuth2 and OIDC

Before OAuth1, it wasn't possible to ensure high level of security during app integration. It used to demand direct user's credential sharing with one solution to access the other.

With OAuth1, role based authentication was now possible, but that requires client side's data handling, which means it wasn't well designed for native apps, mobile apps or iot.

OAuth2 is handling only Authorization, with four agents "Client", "Resource Owner", "Resource Server" and "Authentication Server"

- Client identifies itself to Authentication Server
- CL asks Resource Owner's permission to ask for some data
- Accepted, CL redirects RO to AS's page
- With accepted credentials, AS is giving an Access Token in return
- With Access Token, CL now asks Resource Server for content

OAuth2 is working only with "what will you do?"

Solving the "who you are?" question, we have OpenID Connect
OIDC abstracts credential delivering to Authentication Server

## Authentication

### 4 authentication methods

Knowledge Based _("Something you know")_
    - User/Pass
    - PIN Code

Possesion Based _("Something you have")_
    - SMS or Email
    - Authenticator App

Inheritance Based _("Something you are")_
    - Fingerprint
    - Face Recognition

Location Based _("Somewhere you are")_
    - Geo-fencing
    - IP Address

### Single Sign-On

The concept of one identity for multiple applications. The token validation and permission granting is delegated to a high-security third-party entity called Identity Provider (Google, Microsoft), acting as the Authorization Server. IdP will handle the entire complex identity lifecicle (creation, storage and management).

### JWT

A compact and secure format used for transmitting data between different applications and services. Well stablished method to verify identity and permissions of a user on a service.