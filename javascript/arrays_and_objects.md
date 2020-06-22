# Arrays and objects

## Duplicate an object

Shallow copy an existing object with the help of `Object.assign`:

```javascript
const a = {hello: 'world'};
const b = Object.assign({}, a);
```

## Duplicate an array

### Shallow copy

With the help of the spread operator `...`:

```javascript
const a = [1, 2, 3];
const b = [...a];
```

### First-level deep copy

```javascript
const a = [1, 2, {hello: 'world'}];
const b = a.map(e => Object.assign({}, e));
```
