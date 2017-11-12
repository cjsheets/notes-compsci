# Overview

Security can be a stumbling point for interviewees.

Don't misinterpret "never roll your own cryptography / security" as
"import a library and then don't worry about security". It's important to understand the fundamentals
even if you're not developing security-specific applications.



# Sample Questions

## Authentication

**Q: What is JWT**

**A:** JSON Web Tokens are an open standard (RFC 7519) that describes a method for transmitting
information between parties securely. They are:

* Signed with either HMAC algorithm + secret or RSA pub/private keys so they can be verified/trusted
* Compact enough to send via HTTP header
* Self-contained. The token contains enough information to avoid needing to query the database for user permissions


**Q: Why use JWT**

**A:** JWT contains the claims a server needs to determine user permissions, allowing the server to remain stateless (no
need to store user session state) and prevent the server from having to query the user database.

It can also use session/local storage eliminating CORS issues.


**Q: Describe a JWT**

**A:** JWT consists of 3 parts separated by a '.'

* Header - token type + hash algo
* Payload - claims and metadata
    * reserved claims include iss (issuer), expr (expiration time)
    * public/private claims, user, role, etc
* Signature - signed combo of Base64URL encoded header + encoded paylod + secret


**Q: Describe Secure and HTTP Only Cookies**

**A:** Cookies are inherently vulnerable compared to the Web Storage API. Sensitive data should never be stored in
cookies. Sending `Secure` with `Set-Cookie` forces the cookie to only be returned via HTTPS. HttpOnly prevents access from Document.cookie which protects against XSS.

You can also scope a cookie with Domain and Path directives.


## Cross Origin

**Q: Describe CORS**

**A:** CORS stands for **Cross Origin Resource Sharing**.

It allows users to access server resources when the current page originates from a different domain,
port or protocol than the requested resource. This is done with HTTP headers.

Without CORS headers, browsers don't allow scripts to make Cross origin HTTP requests.

The spec requires browsers to preflight CORS requests with HTTP OPTIONS requests to retrieve the
permissable methods and required auth data. There is a narrow exception for a select few "simple request" types.



## HTTP


**Q: Describe CSP**

**A:** CSP stands for **Content Security Policy**.

It is a security layer implemented by browsers to mitigate XSS and data injection attacks.

CSP allows servers (or HTML meta tags) to define which origins are allowed to source executable scripts, styles,
inline scripts, form actions, frame actions, etc. It can block mixed content and report incidents of XSS attempts.

**Q: How is CSP implemented**

**A:** Specify a policy via HTTP Header. `Content-Security-Policy: default-src 'self'`


**Q: Describe HPKP**

**A:** HTTP Public Key Pinning Extension. Adds a browser-side security measure where a server can
tell a client which public key it should use. Protects against MITM if a CA were compromised.


**Q: Describe HTTP Authorization**

**A:** Along with 401 forbidden, server could provide a WWW-Authenticate header which would cause the client to
ask the user for a password to provide the server on subsequent requests.


**Q: Describe CSRF**

**A:** Cross Site Request Forgery is an attack where commands are sent to a server impersonating a users intent.
An example would be embeding an HTTP request + url parameters in an image SRC.


**Q: Session Hijacking**

**A:** If cookies are available to javascript and HttpOnly isn't set, a site could use document.cookies to make a request
passing your session cookie via HTTP query params.

**Q: What is X-Frame-Options**

**A:** A header indicating whether a browser should render your page in a frame



