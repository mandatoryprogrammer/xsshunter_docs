# XSS Hunter Correlated Injection API Doc
This document is meant to outline the single API endpoint required to build an XSS Hunter compatible correlated injection tool.

### Endpoint
`https://api.xsshunter.com/api/record_injection`
### Content-Type
`application/json`
### Parameters
`request` - This is the request that was performed with the unique `injection_key`. This could be an HTTP request or another protocol.

`owner_correlation_key` - This is the key which is exposed under the "Settings" tab of the XSS Hunter website. It is unique for each account and should not be shared in between users.

`injection_key` - This is the unique key used for each injection, generation of these keys is up to the creator of the tool.

### Example HTTP Request/Response
```http
POST /api/record_injection HTTP/1.1
Host: api.xsshunter.com
User-Agent: xsshunter_client
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
Referer: https://xsshunter.com/app
Content-Length: 196
Connection: close

{"request":"GET / HTTP/1.1...","owner_correlation_key":"XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX", "injection_key":"UNIQUE_REQUEST_KEY"}
```
```http
HTTP/1.1 200 OK
Server: cloudflare-nginx
Date: Thu, 24 Mar 2016 05:06:33 GMT
Content-Type: application/json
Connection: close
X-Xss-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Content-Security-Policy: default-src 'self'
Expires: 0
Cache-Control: no-cache, no-store, must-revalidate
Access-Control-Allow-Methods: OPTIONS, PUT, DELETE, POST, GET
Strict-Transport-Security: max-age=0; includeSubDomains
Pragma: no-cache
Access-Control-Allow-Credentials: true
X-Frame-Options: deny
Access-Control-Allow-Headers: X-CSRF-Token, Content-Type
Access-Control-Allow-Origin: https://xsshunter.com
CF-RAY: 2887982ed5e32864-SJC
Content-Length: 72

{"message": "Injection request successfully recorded!", "success": true}
```

## Example Client
Please see https://github.com/mandatoryprogrammer/xsshunter_client for an example client built off of this API.
