---
title: 'Response status codes'

layout: nil
---

### Success

Successes differ from errors in that their body may not be a simple response object with a code and a message. The headers however are consistent across all calls:

* `GET`, `PUT`, `DELETE` returns `200 OK` on success,
* `POST ` returns 201 on success,

When [retrieving stuff](#get-stuff) for example:

```Status: 200 OK: Successful GET```
```{
    code: 200,
    message: 'Example'
}```
```Status: 201 Created: Successful POST```
```{
    code: 200,
    message: 'Example'
}```

### Error

Error responses are simply returning [standard HTTP error codes](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) along with some additional information:

* The error code is sent back as a status header,
* The body includes an object describing both the code and message (for debugging and/or display purposes),

For a call with an invalid authentication token for example:

```Status: 400 Bad Request: Invalid JSON (can't be parsed or has wrong types).```
```{
    code: 400,
    message: 'Example'
}```
```Status: 401 Unauthorized: The OAuth token is either not provided or invalid.```
```{
    code: 401,
    message: 'Example'
}```
```Status: 404 Not Found: The resource, project, or endpoint being requested doesn’t exist.```
```{
    code: 404,
    message: 'Example'
}```
```Status: 405 Invalid HTTP method: A GET, POST, DELETE, or PUT was sent to an endpoint that doesn’t support that particular verb.```
```{
    code: 405,
    message: 'Example'
}```
```Status: 406 Not Acceptable: Required fields are missing.```
```{
    code: 406,
    message: 'Example'
}```
```Status: 503 Service Unavailable.```
```{
    code: 503,
    message: 'Example'
}```


### Status Codes
The success failure for request is indicated by an HTTP status code. A 2xx status code indicates success, whereas a 4xx status code indicates an error. 

### Exponential Backoff

When a 503 error code is returned, it signifies that the server is currently unavailable. This means there was a problem processing the request on the server-side; it makes no comment on the validity of the request. Libraries and clients should use [exponential backoff](http://en.wikipedia.org/wiki/Exponential_backoff) when confronted with a 503 error, retrying their request with increasing delays until it succeeds or a maximum number of retries (configured by the client) has been reached.



