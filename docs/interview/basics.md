# Javascript Basics




# Sample Questions

## Math

**Q:** Describe what a logarithm is doing

**A:** What power must we raise this base to, in order to get this answer log 10 ( 100 ) = 10 ^ x = 100


**Q:** Why do we use logarithms

**A:** It's useful for time complexity when the problem space is regularly halved. "How many times must we divide our input n in half to reach 1 (or, find the answer)". An example is binary search which takes O( log n ) time or sorting which generally takes O( n log n ).


## Web Communications

**Q:** Describe HTTP

**A:** Hypertext Transfer Protocol is a stateless application layer protocol for system communication.
+ S includes TLS. It follows a client server model.


**Q:** Describe the first line in HTTP

**A:** Method, request target (ie.  "/") and HTTP version


**Q:** What are common transport layer protocols

**A:** TCP, UDP. 


**Q:** What are some common HTTP Response Codes

* 2xx: Successful
    * 200 OK
    * 202 Accepted
* 3xx: Redirection
    * 301 Moved Permanently
* 4xx: Client Error
    * 403 Forbidden
    * 404 Not Found
    * 409 Conflict
* 5xx: Server Error
    * 503 Service Unavailable


**Q:** Describe HTTP Request

**A:** 

* Open TCP connection
* Send HTTP message (human readable prior to v2)
* Read the server response
* Close TCP Connection



**Q:** Describe Content Negotiation

**A:** A server could have several representations of the same document at a particular URL. (different file format, 
language, etc). 

The client could sent a `Accept, Accept-Charset, Accept-Encoding, Accept-Language` header or the server could respond with
HTTP 300 (Multiple Choices) to indicate the client should specify what it wants returned.



**Q:** How could state be maintained in HTTP

**A:** Using cookies


**Q: Describe Cookies**

**A:** Cookies are data provided by the server for users to store and provide back. They're used for:

* session management
* personalization
* tracking

They're set with a `Set-Cookie` header and returned in a `Cookie` header.

They are included in every request so they can degrade performance if used for general data storage.

**Q: What are Cookie alternatives**

**A:** Web storage API (local / session storage)


**Q:** Describe a REST API

**A:** 

An application program interface that uses HTTP requests to GET, PUT, POST and DELETE data.

* REpresentational State Transfer architectural style
* Calls should be stateless and independent
* lookup non-existent object properties.
* function parameters that were not passed.
