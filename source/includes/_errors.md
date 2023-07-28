# HTTP Response Code

The Envio API uses the following http response codes:

| Code | Meaning                                                             |
| ---- | ------------------------------------------------------------------- |
| 200  | Success                                                             |
| 400  | Bad Request -- Your request is invalid, should be valid json format |
| 401  | Unauthorized -- Your API key is invalid.                            |
| 403  | Forbidden                                                           |
| 404  | Not Found -- The specified request could not be found.              |
| 405  | Method Not Allowed -- You tried to access with an invalid method.   |
| 422  | Unprocessable Entity -- Your input not pass our validation process  |
| 429  | Too Many Requests -- You're requesting too many request             |
| 500  | Internal Server Error -- We had a problem with our server.          |
