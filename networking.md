[All questions](README.md)

# Networking
+ [What is __http__ in networking?](#what-is-http-in-networking)
+ [What is __https__ in networking?](#what-is-https-in-networking)
+ [What are HTTP status codes?](#What-are-HTTP-status-codes)

[Table of content](#networking)

###What is __http__ in networking?
HTTP means HyperText Transfer Protocol. 
HTTP is the underlying protocol used by the World Wide Web and this protocol defines how messages are formatted and transmitted, 
and what actions Web servers and browsers should take in response to various commands.<BR/>
HTTP is an client-server protocol that allows clients to request web pages from web servers. 
It is an application level protocol widely used on the Internet. 
Clients are usually web browsers. When a user wants to access a web page, a browser sends an HTTP Request message to the web server.
 The server responds with the requested web page.

[Table of content](#networking)

###What is __https__ in networking?
HTTPS(Hypertext Transfer Protocol Secure) is a secure version of HTTP. 
This protocol enables secure communication between a client (e.g. web browser) and a server (e.g. web server) by using encryption. 
HTTPS uses Transport Layer Security (TLS) protocol or its predecessor Secure Sockets Layer (SSL) for encryption.<BR/>
HTTPS is commonly used to create a secure channel over some insecure network, e.g. Internet. 
A lot of traffic on the Internet is unencryped and susceptible to sniffing attacks. 
HTTPS encrypts sensitive information, which makes a connection secure.<BR/>
HTTPS URLs begin with `https` instead of `http`.

[Table of content](#networking)

### What is default port for http and https?
By default, __HTTP__ uses port __80__ and __HTTPS__ uses port __443__,<BR/> 
HTTPS uses a well-known TCP port 443. 
If the port is not specified in a URL, browsers will use this port when sending HTTPS request.

[Table of content](#networking)

### What are HTTP status codes?
When a client makes a request to an HTTP server — and the server successfully receives the request — 
the server must notify the client if the request was successfully handled or not. 
HTTP accomplishes this with five categories of status codes:

* 100-level (Informational) — Server acknowledges a request
* 200-level (Success) — Server completed the request as expected
* 300-level (Redirection) — Client needs to perform further actions to complete the request
* 400-level (Client error) — Client sent an invalid request
* 500-level (Server error) — Server failed to fulfill a valid request due to an error with server

[Table of content](#networking)

### Name some com,mon response codes
Some common response codes include:
* 400 Bad Request — Client sent an invalid request — such as lacking required request body or parameter
* 401 Unauthorized — Client failed to authenticate with the server
* 403 Forbidden — Client authenticated but does not have permission to access the requested resource
* 404 Not Found — The requested resource does not exist
* 412 Precondition Failed — One or more conditions in the request header fields evaluated to false
* 500 Internal Server Error — A generic error occurred on the server
* 503 Service Unavailable — The requested service is not available

[All questions](README.md)