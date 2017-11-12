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


## Cross Origin

**Q: Describe CORS**

**A:** CORS stands for **Cross Origin Resource Sharing**.

It allows users to access server resources when the current page originates from a different domain,
port or protocol than the requested resource. This is done with HTTP headers.

Without CORS headers, browsers don't allow scripts to make Cross origin HTTP requests.

The spec requires browsers to preflight CORS requests with HTTP OPTIONS requests to retrieve the
permissable methods and required auth data. There is a narrow exception for a select few "simple request" types.


