# Google Firebase dynamic linking

## Dynamic link: 

To create a dynamic link, go to `Firebase console > left menu > Grow > click Dynamic Links`. 

Example of short-url dynamic link: `https://minsh.page.link/ZCg5`. 

This short-url displays different content based on the request headers sent from the client. We found different content returned when using `curl` or using a desktop browser.

### From curl

Redirect to social network preview page: `https://minsh.page.link/s?socialDescription&socialImageUrl=https://premium.minsh.com/images/logo.png&socialTitle=Group+123`

This is what is served when the url is pasted into a social network text input.
The social network backend is fetching the content of the url to display a title and a thumbnail image in the feed.

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

Redirect to `https://premium.minsh.com/group/123`, the actual page.




