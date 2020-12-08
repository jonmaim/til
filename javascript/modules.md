# Modules

```javascript
<script src="./js/index.js" type="module"></script>
```

Modules are always deferred. They wait until the HTML document is fully ready, and then run. 
As a side-effect, module scripts always 'see' the fully loaded HTML-page.

In the browser, import must get either a relative or absolute URL, i.e., no *bare* module import.
