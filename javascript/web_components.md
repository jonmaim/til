# Web components

HTML has always lacked a way to automatically associate JS behavior with markup until native and _custom_ HTML _elements_, i.e., custom elements.

Here is a barebone example of custom element definition:

```javascript
customElements.define('spinner-button', class extends HTMLElement {...});
```

In more details:

```javascript
class SpinnerButton extends HTMLElement {
    
  /* reflecting properties: attributes */
  get disabled() { return this.hasAttribute('disabled'); }
  set disabled(val) {
    if (val) {
      this.setAttribute('disabled', '');
    } else {
      this.removeAttribute('disabled');
    }
  }
  
  /* custom element reactions */
  connectedCallback() {
    console.log('ℹ️ inserted into the DOM');  
  }
  disconnectedCallback() {
    console.log('ℹ️ removed into the DOM');  
  }
  attributeChangedCallback(attrName, oldVal, newVal) {
    console.log(`ℹ️ an observed attribute value (${attrName}) is modified from ${oldVal} to ${newVal}`);
    if (this.disabled) {
      this.setAttribute('aria-disabled', 'true');
    }
  }
  
  constructor() {
    /* mandatory */
    super();
        
    this.addEventListener('click', e => {
      console.log('🐭');
    });
  }
  
}

/* a custom element _must_ include a mandatory `-` in his name */
customElements.define('spinner-button', SpinnerButton);
```

Inside a class definition `this`  refers to the DOM element instance itself.

## Using a shadow DOM

A shadow DOM provides a way for an element to own, render, and style a chunk of DOM that's separate from the rest of the page. 

### Declaring DOM fragment

`<template>` allows to define DOM fragment to be parsed and used later on.

```javascript
let tmpl = document.createElement('template');
tmpl.innerHTML = `
  <style>
    button { 
      color: red;
    }
  </style>
  
  <button>
    <slot></slot>
  </button>
`;
```

Style encapsulation is defined as `document` > `element (shadow host)` > `shadow root` > `contents`

# Outline

 * bare-bone basics introduction: custom elements with shadow DOM
 * higher-level libraries to avoid the boilerplate: 
   * lit-html + lit-element: typescript. well commented. many files probably around 2500 lines. needs a module bundler.
   * µhtml + µce: javascript. 2 files totaling 2 x 1250 lines. no module bundler needed and can be used as-is as there is no bare-bone module called.
 
# References

 * [https://developers.google.com/web/fundamentals/web-components/customelements](https://developers.google.com/web/fundamentals/web-components/customelements)
