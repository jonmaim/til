# CSS foundations

## block, inline-block andd inline display properties

| display | vertical margin | horizontal expansion | tags with default |
|--|:-:|--|--|
| block | ✅ | take up whole available width | `<h1>`, `<h2>`, ... |
| inline-block | ✅ | just enough to contain self content | `<button>`, ... |
| inline | ❌ | just enough to contain self content | `<em>`, `<strong>`, `<img>`, ... |

## overriding img default reset

`<img>` is `display: inline;` by default, which means there is no vertical margins available.

```scss
img {
  display: block;
  max-width: 100%; // do not break out parent container
}
```

## dimensions calculation

| box-sizing | dimension  |
|--|--|
| content-box | width or height property + padding + border |
| border-box | width or height property |

## using relative units instead of absolute ones like `px`

| unit | `font-size` property | other properties |
|--|--|--|
| em | relative to the `font-size` of the **parent** element | relative to the `font-size` of the **current** element |
| rem | relative to the `font-size` of the **root** `html` element | relative to the `font-size` of the **root** `html` element |

## `::before` and `::after` pseudo-elements

| keyword | name | example |
|--|--|--|
| `::` | pseudo-element | `div::before` |
| `:` | pseudo-selector | `div:nth-child(odd)` |

```scss
div::before {
  content: "before";
}
div::after {
  content: "after";
}
```
```html
<div>
  before
  <!-- Rest of stuff inside the div -->
  after
</div>
```
