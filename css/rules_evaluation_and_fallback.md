# CSS rules evalution and fallback

It is valid to write the same CSS rule multiple times. 
Rules that are not understood by a device / OS / browser are skipped. 
The last understood value is the one used as fallback. 

```scss
.page {
  position: relative;
  height: calc(100% - 50px); /* iOS 10 on iPad fallback */
  height: calc(100% - 50px - constant(safe-area-inset-bottom)); /* iOS 11 on iPhone with notch fallback */
  height: calc(100% - 50px - env(safe-area-inset-bottom)); /* iOS 11.2+ on iPhone with notch fallback */
}
```
☮️
