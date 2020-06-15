# Google Firebase dynamic linking

## Dynamic link: 

To create a dynamic link, go to `Firebase console > left menu > Grow > click Dynamic Links`. 

Example of short-url dynamic link: `https://minsh.page.link/ZCg5`. 

This short-url displays different content based on the request headers sent from the client. We found different content returned when using `curl` or using a desktop browser.

### From curl

Redirect to social network preview page: `https://minsh.page.link/s?socialDescription&socialImageUrl=https://premium.minsh.com/images/logo.png&socialTitle=Group+123`

This is what is served when the url is pasted into a social network text input.
The social network backend is fetching the content of the url to display a title and a thumbnail image in the feed. 
See `open graph` meta tags:

```html
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

### From browser

Redirect to `https://premium.minsh.com/group/123`, the actual page we configured for this dynamic link.

## Dynamic link host

Our host is `https://minsh.page.link`. A dynamic link host will provide more information at this url: `https://minsh.page.link/.well-known/assetlinks.json`

```json
[{
    "relation":["delegate_permission/common.handle_all_urls"],
    "target":{
      "namespace":"android_app",
      "package_name":"com.minsh.minshpremium",
      "sha256_cert_fingerprints":["EA:B0:E7:F8:B6:27:5E:9F:49:D2:BD:47:C7:F2:D2:52:B3:76:4D:02:F1:DC:91:F4:06:4E:28:97:F3:8B:E1:17"]
    }
}]
```


