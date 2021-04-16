# Promises

## Converting `async.mapSeries` to a `Promise`

```js
async.mapsSeries([1, 2, 3], (idx, cb) => {
  cb(null, idx);
}, (err, results) => {
  /* result is an array of ids */
  console.log(results);
});
```

```js
let current = Promise.resolve();
Promise.all([1, 2, 3].map(idx => {
  current = current.then(() => {
    return idx;
  });
  return current;
})).then(results => {
  /* result is an array of ids */
  console.log(results);
});
```

## References

[Promise nuggets](https://promise-nuggets.github.io/)
