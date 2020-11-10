# Optional chaining

With EcmaScript 2020, which is supported in NodeJS 14 you can use optional chaining:

Instead of writing this: 

```javascript
if (!app.notifications || !app.notifications.ios || app.notifications.ios.apns || !app.notifications.ios.apns.key) { 
  /* ... */ 
}
```

You can simply write this: 

```javascript
if (!app.notifications?.ios?.apns?.key) { 
  /* ... */
}
```

From [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining):

The `?.` operator functions similarly to the `.` chaining operator, 
except that instead of causing an error if a reference is nullish (null or undefined), 
the expression short-circuits with a return value of undefined.

## Bracket notation

A dot (`?.[x]`) needs to be used before the opening bracket: 
```
const value = a?.[b]?.c;
```

## Optional chaining with functions

When not sure if a function is going to be present at run-time: use optional chaining when calling it.
```
const result = api.method?.();
```
The expression `api.method?.()` will return `undefined` if `method` does not exists (instead of throwing an exception).

## VSCode integration

Add the following config to your `.eslintrc.json` file:
```
"parser": "babel-eslint"
```
