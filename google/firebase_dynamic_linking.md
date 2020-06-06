# Google Firebase dynamic linking

## Dynamic link: 

`https://minsh.page.link/ZCg5`. 

This short-url displays different content based on the request headers sent from the client. We found different content returned when using `curl` or using a desktop browser.

Let's see what's inside this short url with a `curl` user-agent:
```
$ curl -i https://minsh.page.link/ZCg5

HTTP/1.1 302 Found
...
Location: https://minsh.page.link/s?socialDescription&socialImageUrl=https://premium.minsh.com/images/logo.png&socialTitle=Group+123
...
```
From a `curl` it is a 302 redirection to `https://minsh.page.link/s?socialDescription&socialImageUrl=https://premium.minsh.com/images/logo.png&socialTitle=Group+123`

This is a `curl` request simulating a desktop browser:
```
curl -i 'https://minsh.page.link/ZCg5?_imcp=1'   -H 'authority: minsh.page.link'   -H 'pragma: no-cache'   -H 'cache-control: no-cache'   -H 'upgrade-insecure-requests: 1'   -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.138 Safari/537.36'   -H 'accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9'   -H 'sec-fetch-site: same-origin'   -H 'sec-fetch-mode: navigate'   -H 'sec-fetch-dest: document'   -H 'referer: https://minsh.page.link/'   -H 'accept-language: en-GB,en-US;q=0.9,en;q=0.8'   -H 'cookie: OTZ=5484100_34_34__34_'   --compressed

HTTP/1.1 302 Found
...
Location: https://premium.minsh.com/group/123
...
```



This is the result from a `curl` `user-agent`:
```
curl -i "https://minsh.page.link/s?socialDescription&socialImageUrl=https://premium.minsh.com/images/logo.png&socialTitle=Group+123"

HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: Mon, 01 Jan 1990 00:00:00 GMT
Date: Fri, 05 Jun 2020 17:05:12 GMT
Content-Security-Policy: script-src 'nonce-Voz20eMdCenAFYS2K5yq1g' 'unsafe-inline';object-src 'none';base-uri 'self';report-uri /_/DurableDeepLinkUi/cspreport;worker-src 'self'
Server: ESF
X-XSS-Protection: 0
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
Alt-Svc: h3-27=":443"; ma=2592000,h3-25=":443"; ma=2592000,h3-T050=":443"; ma=2592000,h3-Q050=":443"; ma=2592000,h3-Q049=":443"; ma=2592000,h3-Q048=":443"; ma=2592000,h3-Q046=":443"; ma=2592000,h3-Q043=":443"; ma=2592000,quic=":443"; ma=2592000; v="46,43"
Accept-Ranges: none
Vary: Accept-Encoding
Transfer-Encoding: chunked

<!DOCTYPE html><html>
  <head>
      <meta name="twitter:card" content="summary_large_image"/>
      <title>Group 123</title>
      <meta property="og:title" content="Group 123"/>
      <meta name="twitter:title" content="Group 123"/>
      <meta property="og:image" content="https://premium.minsh.com/images/logo.png"/>
      <meta name="twitter:image" content="https://premium.minsh.com/images/logo.png"/>
   </head>
</html>
```
This is what is served when the url is pasted into a social network input.
The social network backend is fetching the content of the url to display a title and a thumbnail image in the feed.

```
curl 'https://minsh.page.link/s?socialDescription&socialImageUrl=https://premium.minsh.com/images/logo.png&socialTitle=Group+123' -H 'authority: minsh.page.link' -H 'pragma: no-cache' -H 'cache-control: no-cache' -H 'upgrade-insecure-requests: 1' -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Safari/537.36' -H 'sec-fetch-dest: document' -H 'accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9' -H 'sec-fetch-site: none' -H 'sec-fetch-mode: navigate' -H 'sec-fetch-user: ?1' -H 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' --compressed

```

## https://premium.minsh.com/group/123 📱+ 💻
```
HTTP/1.1 404 Not Found
Content-Type: text/html; charset=utf-8
Content-Length: 535
Connection: keep-alive
Date: Sat, 06 Jun 2020 16:15:45 GMT
Server: AmazonS3
X-Cache: Error from cloudfront
Via: 1.1 9c958dcd7cfe69b7305581ffd7680ca3.cloudfront.net (CloudFront)
X-Amz-Cf-Pop: MAA50-C1
X-Amz-Cf-Id: dPqOeWDEtA3CgLi0tpiZR3jL-Bopov7H-ex5QoSKMMfeB9JFAxaU8Q==
Age: 219

<html>
<head><title>404 Not Found</title></head>
<body>
<h1>404 Not Found</h1>
<ul>
<li>Code: NoSuchKey</li>
<li>Message: The specified key does not exist.</li>
<li>Key: group/123</li>
<li>RequestId: 2AD4F43C70F9DC89</li>
<li>HostId: +LLo2/RScRtomdHHW6qP0AjdG7igcAiVNOUs/w0F+4WjsHMqOHcj0nLrY8ajtDq4VOiEi6ihPWQ=</li>
</ul>
<h3>An Error Occurred While Attempting to Retrieve a Custom Error Document</h3>
<ul>
<li>Code: NoSuchKey</li>
<li>Message: The specified key does not exist.</li>
<li>Key: 404.html</li>
</ul>
<hr/>
</body>
</html>
```
