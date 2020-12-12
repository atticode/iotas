#+TITLE: HTTP Header 参数列表

** Request Header fields

| 参数名                         | 说明                              | 示例                                                                                              |
|--------------------------------+-----------------------------------+---------------------------------------------------------------------------------------------------|
| Accept                         | 接收的内容类型                    | Accept: text/plain                                                                                |
| Accept-Charset                 | 接收的字符编码                    | Accept-Charset: utf-8                                                                             |
| Accept-Datetime                | 接受的版本时间                    | Accept-Datetime: Thu, 31 May 2007 20:35:00 GMT                                                    |
| Accept-Encoding                | 接受的编码格式                    | Accept-Encoding: gzip, deflate                                                                    |
| Accept-Language                | 接受的语言                        | Accept-Language: zh-CN                                                                            |
| Authorization                  | HTTP 身份验证的凭证               | Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==                                                 |
| Access-Control-Request-Method  |                                   | Access-Control-Request-Method: GET                                                                |
| Access-Control-Request-Headers |                                   | Access-Control-Request-Method: GET                                                                |
| Cache-Control                  |                                   | Cache-Control: no-cache  或  Connection: Upgrade                                                  |
| Connection                     |                                   | Connection: keep-alive                                                                            |
| Cookie                         |                                   | Cookie: $Version=1; Skin=new;                                                                     |
| Content-Length                 | 请求体的字节数                    | Content-Length: 321                                                                               |
| Content-MD5                    | 请求体的base64编码的MD5值         | Content-MD5: Q2hlY2sgSW50ZWdyaXR5IQ==                                                             |
| Content-Type                   | 请求体的内容类型(POST或PUT请求时) | Content-Type: application/x-www-form-urlencoded                                                   |
| Date                           |                                   | Date: Tue, 15 Nov 1994 08:12:31 GMT                                                               |
| Expect                         |                                   | Expect: 100-continue                                                                              |
| Forwarded                      |                                   | Forwarded: for=192.0.2.60;proto=http;by=203.0.113.43 Forwarded: for=192.0.2.43, for=198.51.100.17 |
| From                           |                                   | From: user@example.com                                                                            |
| Host                           |                                   | Host: en.wikipedia.org                                                                            |
| If-Match                       |                                   | If-Match: "737060cd8c284d8af7ad3082f209582d"                                                      |
| If-Modified-Since              |                                   | If-Modified-Since: Sat, 29 Oct 1994 19:43:31 GMT                                                  |
| If-None-Match                  |                                   | If-None-Match: "737060cd8c284d8af7ad3082f209582d"                                                 |
| If-Range                       |                                   | If-Range: "737060cd8c284d8af7ad3082f209582d"                                                      |
| If-Unmodified-Since            |                                   | If-Unmodified-Since: Sat, 29 Oct 1994 19:43:31 GMT                                                |
| Max-Forwards                   |                                   | Max-Forwards: 10                                                                                  |
| Origin                         |                                   | Origin: http://www.example-social-network.com                                                     |
| Pragma                         |                                   | Pragma: no-cache                                                                                  |
| Proxy-Authorization            |                                   | Proxy-Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==                                           |
| Range                          |                                   | Range: bytes=500-999                                                                              |
| Referer                        |                                   | Referer: http://en.wikipedia.org/wiki/Main_Page                                                   |
| TE                             |                                   | TE: trailers, deflate                                                                             |
| User-Agent                     |                                   | User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:12.0) Gecko/20100101 Firefox/12.0                  |
| Upgrade                        |                                   | Upgrade: HTTPS/1.3, IRC/6.9, RTA/x11, websocket                                                   |
| Via                            |                                   | Via: 1.0 fred, 1.1 example.com (Apache/1.1)                                                       |
| Warning                        |                                   | Warning: 199 Miscellaneous warning                                                                |
|                                |                                   |                                                                                                   |
| ---其他                        |                                   |                                                                                                   |
| X-Requested-With               |                                   | X-Requested-With: XMLHttpRequest                                                                  |
| DNT                            |                                   | DNT: 1 (Do Not Track Enabled)                                                                     |
| X-Forwarded-For                |                                   | X-Forwarded-For: client1, proxy1, proxy2                                                          |
| X-Forwarded-Host               |                                   | X-Forwarded-Host: en.wikipedia.org                                                                |
| X-Forwarded-Proto              |                                   | X-Forwarded-Proto: https                                                                          |
| Front-End-Https                |                                   | Front-End-Https: on                                                                               |
| X-Http-Method-Override         |                                   | X-HTTP-Method-Override: DELETE                                                                    |
| X-ATT-DeviceId                 |                                   | X-Att-Deviceid: GT-P7320/P7320XXLPG                                                               |
| X-Wap-Profile                  |                                   | x-wap-profile: http://wap.samsungmobile.com/uaprof/SGH-I777.xml                                   |
| Proxy-Connection               |                                   | Proxy-Connection: keep-alive                                                                      |
| X-UIDH                         |                                   | X-UIDH: ...                                                                                       |
| X-Csrf-Token                   |                                   | X-Csrf-Token: i8XNjC4b8KVok4uw5RftR38Wgp2BFwql                                                    |
| X-Request-ID, X-Correlation-ID |                                   | X-Request-ID: f058ebd6-02f7-4d3f-942e-904344e8cde5                                                |


** Response fields

| 参数名                           | 说明             | 示例                                                                                                                            |
|----------------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------|
| Access-Control-Allow-Origin      |                  | Access-Control-Allow-Origin: *                                                                                                  |
| Access-Control-Allow-Credentials |                  |                                                                                                                                 |
| Access-Control-Expose-Headers    |                  |                                                                                                                                 |
| Access-Control-Max-Age           |                  |                                                                                                                                 |
| Access-Control-Allow-Methods     |                  |                                                                                                                                 |
| Access-Control-Allow-Headers     |                  |                                                                                                                                 |
| Accept-Patch                     |                  | Accept-Patch: text/example;charset=utf-8                                                                                        |
| Accept-Ranges                    |                  | Accept-Ranges: bytes                                                                                                            |
| Age                              |                  | Age: 12                                                                                                                         |
| Allow                            |                  | Allow: GET, HEAD                                                                                                                |
| Alt-Svc                          |                  | Alt-Svc: http/1.1="http2.example.com:8001"; ma=7200                                                                             |
| Cache-Control                    |                  | Cache-Control: max-age=3600                                                                                                     |
| Connection                       |                  | Connection: close                                                                                                               |
| Content-Disposition              |                  | Content-Disposition: attachment; filename="fname.ext"                                                                           |
| Content-Encoding                 |                  | Content-Encoding: gzip                                                                                                          |
| Content-Language                 |                  | Content-Language: da                                                                                                            |
| Content-Length                   |                  | Content-Length: 348                                                                                                             |
| Content-Location                 |                  | Content-Location: /index.htm                                                                                                    |
| Content-MD5                      |                  | Content-MD5: Q2hlY2sgSW50ZWdyaXR5IQ==                                                                                           |
| Content-Range                    |                  | Content-Range: bytes 21010-47021/47022                                                                                          |
| Content-Type                     | 内容的 MIME 类型 | Content-Type: text/html; charset=utf-8                                                                                          |
| Date                             |                  | Date: Tue, 15 Nov 1994 08:12:31 GMT                                                                                             |
| ETag                             |                  | ETag: "737060cd8c284d8af7ad3082f209582d"                                                                                        |
| Expires                          |                  | Expires: Thu, 01 Dec 1994 16:00:00 GMT                                                                                          |
| Last-Modified                    |                  | Last-Modified: Tue, 15 Nov 1994 12:45:26 GMT                                                                                    |
| Link                             |                  | Link: </feed>; rel="alternate"                                                                                                  |
| Location                         |                  | Location: http://www.w3.org/pub/WWW/People.html                                                                                 |
| P3P                              |                  | P3P: CP="This is not a P3P policy! See http://www.google.com/support/accounts/bin/answer.py?hl=en&answer=151657 for more info." |
| Pragma                           |                  | Pragma: no-cache                                                                                                                |
| Proxy-Authenticate               |                  | Proxy-Authenticate: Basic                                                                                                       |
| Public-Key-Pins                  |                  | Public-Key-Pins: max-age=2592000; pin-sha256="E9CZ9INDbd+2eRQozYqqbQ2yXLVKB9+xcprMF+44U1g=";                                    |
| Retry-After                      |                  | Retry-After: Fri, 07 Nov 2014 23:59:59 GMT                                                                                      |
| Server                           |                  | Server: Apache/2.4.1 (Unix)                                                                                                     |
| Set-Cookie                       |                  | Set-Cookie: UserID=JohnDoe; Max-Age=3600; Version=1                                                                             |
| Strict-Transport-Security        |                  | Strict-Transport-Security: max-age=16070400; includeSubDomains                                                                  |
| Trailer                          |                  | Trailer: Max-Forwards                                                                                                           |
| Transfer-Encoding                |                  | Transfer-Encoding: chunked                                                                                                      |
| Tk                               |                  | Tk: ?                                                                                                                           |
| Upgrade                          |                  | Upgrade: HTTPS/1.3, IRC/6.9, RTA/x11, websocket                                                                                 |
| Vary                             |                  | Vary: *                                                                                                                         |
| Via                              |                  | Via: 1.0 fred, 1.1 example.com (Apache/1.1)                                                                                     |
| Warning                          |                  | Warning: 199 Miscellaneous warning                                                                                              |
| WWW-Authenticate                 |                  | WWW-Authenticate: Basic                                                                                                         |
| X-Frame-Options                  |                  | X-Frame-Options: deny                                                                                                           |
|                                  |                  |                                                                                                                                 |
| --其他                           |                  |                                                                                                                                 |
| Content-Security-Policy          |                  | X-WebKit-CSP: default-src 'self'                                                                                                |
| Refresh                          |                  | Refresh: 5; url=http://www.w3.org/pub/WWW/People.html                                                                           |
| Status                           |                  | Status: 200 OK                                                                                                                  |
| Timing-Allow-Origin              |                  | Timing-Allow-Origin: *                                                                                                          |
| Upgrade-Insecure-Requests        |                  | Upgrade-Insecure-Requests: 1                                                                                                    |
| X-Content-Duration               |                  | X-Content-Duration: 42.666                                                                                                      |
| X-Content-Type-Options           |                  | X-Content-Type-Options: nosniff                                                                                                 |
| X-Powered-By                     |                  | X-Powered-By: PHP/5.4.0                                                                                                         |
| X-Request-ID, X-Correlation-ID   |                  | X-Request-ID: f058ebd6-02f7-4d3f-942e-904344e8cde5                                                                              |
| X-UA-Compatible                  |                  | X-UA-Compatible: Chrome=1                                                                                                       |
| X-XSS-Protection                 |                  | X-XSS-Protection: 1; mode=block                                                                                                                                |



- [[https://en.wikipedia.org/wiki/List_of_HTTP_header_fields][WikiPedia List of HTTP header fields]]
- [[https://www.w3.org/Protocols/rfc2616/rfc2616.html][W3C Hypertext Transfer Protocol -- HTTP/1.1]]
- [[https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html][W3C HTTP Header Field Definitions]] 
- [[https://en.wikipedia.org/wiki/Media_type][Wiki Media-Type]]
- [[http://tool.oschina.net/commons][Http Content-Type]]

- [[https://kb.cnblogs.com/page/92320/][博客园 http fields]]
- [[https://www.cnblogs.com/widget90/p/7650890.html][博客园 http fields]]
