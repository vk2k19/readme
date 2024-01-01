# Web component
A web component is reusable custom structure element with specified behavior.
It avoids complexity and collision occurs during reuse of component multiple times on page.
Created by using following methodologies together 
- `customElement` 
- `shadowDom` and 
- `HTML templates`

## Creating Component

### Use `ES6` a.k.a `ES2015` class syntax to create your component and add styles and behavior.
> `class <your-component-name> extends <Native-HTML-ELEMENT-CLASS> {...}`

#### Class can have following life cycle methods:
1. `connectedCallback` : method gets called when custom element is added in DOM first time.
1. `disconnectedCallback`: method gets called when custom element is removed from DOM time.
1. `adoptedCallback`: When element gets moved from one document to another.
1. `attributeChangedCallback`: Whenever any attribute of element is added, updated and removed.

### Register your component in `CustomElementRegistry`.
> `CustomElementRegistry.define()` or
> `customElements.define()` // customElements is exposure of CustomElementRegistry in window.

#### `CustomElementRegistry.define` takes following three arguments:
1. dash separated name to use for custom element e.g `error-text`
1. class which creates this component e.g. `ErrorText` where is implemented as `class ErrorText extends HTMLElement {...}`
1. Object representing which element is extended. This used only when we are using an existing html element with custom behavior. e.g `{ extends: 'p' }`

### It's a good idea to use shadow dom to obtain isolation for component content and styles. Done via 
> `Element.attachShadow()`

#### `Element.attachShadow`
- Takes option which allows access to shadow content via methods
> `{mode: 'open'}` //open or close
- `Event.composed` //true or false, true when an event is triggered from elements inside shadowDom.
- `Event.composedPath()` returns list of elements on which listeners will be invoked.
With shadowRoot with mode `open` it returns path (dom tree path) including elements in shadowRoot for `close` elements inside shadowRoot are not considered .

- To have complex structure use `<template>` and `<slot>` HTML elements.

## Autonomous component
Component which extend generic `HTMLElement` class and create a fresh element.

Example: We will create a simple component which adds red text on white background.

```js
// creation of custom element
class ErrorText extends HTMLElement {
    constructor () {
        super();

        const shadowRoot = this.attachShadow({mode: 'open'});
        const wrapper = document.createElement('span');
        
        wrapper.setAttribute('class', 'error');
        wrapper.textContent = this.textContent;
        const styles = document.createElement(style);
        style.textContent = `
            .error {
                background: white;
                color: red;
            }
        `;

        shadowRoot.appendChild(styles);
        shadowRoot.appendChild(wrapper);
    }
}

// register custom element
customElements.define('error-text', ErrorText);

// use custom element in page
<error-text>this is error</error-text>
```

## Customized built-in component 
Component which extends any standard HTML element with new custom behavior and appearance.
Example: We will edit above component which turns paragraph to error-text-in-p.

```js
// creation of custom element
class ErrorInP extends HTMLParagraphElement {
    constructor () {
        super();
        const wrapper = this;
        
        wrapper.setAttribute('class', 'error');
        const styles = document.createElement('style');
        styles.textContent = `
            .error {
                background: white;
                color: red;
            }
        `;

        wrapper.appendChild(styles);
    }
}

// register element
customElements.define('error-text-in-p', ErrorInP, { extends: 'p' });

// use in markup
<p is='error-text-in-p'>Error copy</p>
```
## Difference between Autonomous and Customized Markup:

### The way the are incorporated in html 
- custom tag is used for Autonomous while 
- customized use the extended element with is attribute with custom-element-name.

### While creating class
- Autonomous extends base HTMLElement
- Customized extends specific element like `HTMLAnchorElement` or `HTMLUListElement`


## Reference:
[Web Components | MDN](https://developer.mozilla.org/en-US/docs/Web/Web_Components)

***

[Go back to homepage](../)
