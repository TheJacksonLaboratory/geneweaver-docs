
Hypertext Transfer Protocol (HTTP) is a stateless application-level protocol used for 
communication between web servers and clients, allowing for the transfer of data and 
requests for resources over the internet. This document summarizes two important
sources of information for HTTP standards:

- The Mozilla Developer Network (MDN) HTTP Reference[^1]
- The HTTP Semantics RFC (RFC 9110)[^2]

## HTTP Methods

### Common Implementation Methods
The following methods are commonly used for the endpoints we create in our web APIs. 
They are useful for creating semantically meaningful RestFUL APIs.

| Method  | Type                  | Description                                                                                                                     |
|---------|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| GET     | Read Only, Idempotent | The GET method requests a representation of the specified resource. Requests using GET should **only retrieve data.**           |
| HEAD    | Read Only, Idempotent | The HEAD method asks for a response identical to a GET request, but **without the response body**.                              |
| POST    | Non-idempotent        | The POST method submits an entity to the specified resource, often **causing a change in state** or side effects on the server. |
| PUT     | Idempotent            | The PUT method **replaces** all current representations of the target resource with the request payload.                        |
| DELETE  | Idempotent            | The DELETE method **deletes** the specified resource.                                                                           |
| PATCH   | Non-idempotent        | The PATCH method applies **partial modifications** to a resource.                                                               |

### Common Operational Methods
These methods are most commonly handled by the web-frameworks/web-server and are not
typically used when implementing our own endpoints.

| Method  | Description                                                                               |
|---------|-------------------------------------------------------------------------------------------|
| CONNECT | The CONNECT method establishes a tunnel to the server identified by the target resource.  |
| OPTIONS | The OPTIONS method describes the communication options for the target resource.           |
| TRACE   | The TRACE method performs a message loop-back test along the path to the target resource. |


## HTTP Response Status Codes
We will list only the most relevant status codes here, but in general, we follow
the [mozilla guidelines](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status). The 
following descriptions are taken directly from the mozilla documentation.



### 2xx Success
These codes indicate success. The three most common that we use are listed here, and 
have only slight differences. 

| Status Code | Description | Long Description                                                                                                                                               |
|-------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200         | OK          | The request succeeded. The result meaning of "success" depends on the HTTP method.                                                                             |
| 201         | Created     | The request succeeded, and a new resource was created as a result. This is typically the response sent after POST requests, or some PUT requests.              |
| 204         | No Content  | There is no content to send for this request, but the headers may be useful. The user agent may update its cached headers for this resource with the new ones. |

### 4xx Client Error
These codes indicate that the server determined that client did something wrong with the
request. These are the most straightforward to implement from a backend perspective,
and provide the most information to the client about what went wrong.

| Status Code | Description          | Long Description                                                                                                                                                                                                                                                                                                                    |
|-------------|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 400         | Bad Request          | The server cannot or will not process the request due to something that is perceived to be a client error (e.g., malformed request syntax, invalid request message framing, or deceptive request routing).                                                                                                                          |
| 401         | Unauthorized         | Although the HTTP standard specifies "unauthorized", semantically this response means "unauthenticated". That is, the client must authenticate itself to get the requested response.                                                                                                                                                |
| 403         | Forbidden            | The client does not have access rights to the content; that is, it is unauthorized, so the server is refusing to give the requested resource. Unlike 401 Unauthorized, the client's identity is known to the server.                                                                                                                |
| 404         | Not Found            | The server cannot find the requested resource. In the browser, this means the URL is not recognized. In an API, this can also mean that the endpoint is valid but the resource itself does not exist. Servers may also send this response instead of 403 Forbidden to hide the existence of a resource from an unauthorized client. |
| 405         | Method Not Allowed   | The request method is known by the server but is not supported by the target resource. For example, an API may not allow calling DELETE to remove a resource.                                                                                                                                                                       |
| 409         | Conflict             | This response is sent when a request conflicts with the current state of the server.                                                                                                                                                                                                                                                |
| 422         | Unprocessable Entity | The request was well-formed but was unable to be followed due to semantic errors.                                                                                                                                                                                                                                                   |

### 5xx Server Error
These codes indicate that the server had a problem processing the request. These are
the most difficult to implement from a backend perspective, and provide the least
information to the client about what went wrong. In general, when using one of these
codes, backend APIs should both log the associated error, and provide as much meaningful
information as possible to the client.

| Status Code | Description            | Long Description                                                                                                                                                                                |
|-------------|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 500         | Internal Server Error  | Internal Server Error                                                                                                                                                                           |
| 501         | Not Implemented        | The request method is not supported by the server and cannot be handled. The only methods that servers are required to support (and therefore that must not return this code) are GET and HEAD. |
| 502         | Bad Gateway            | This error response means that the server, while working as a gateway to get a response needed to handle the request, got an invalid response.                                                  |
| 504         | Gateway Timeout        | This error response is given when the server is acting as a gateway and cannot get a response in time.                                                                                          |


[^1]: [Mozilla: HTTP Status](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
[^2]: [RFC 9110 HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110)
