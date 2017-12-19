# Vue Spinner Component

[Demo](http://sergeyloysha.github.io/vue-spinner-component/)

## Usage

```html
<spinner
  :status="spinnerStatus"
  :color="spinnerColor"
  :size="spinnerSize"
  :depth="spinnerDepth"
  :rotation="spinnerRotation"
  :speed="spinnerSpeed"></spinner>
```

## Installation

### NPM
```bash
$ npm install vue-spinner-component
```

### CommonJS
```js
var Spinner = require('vue-spinner-component/src/Spinner.vue');

new Vue({
  components: {
    Spinner
  }
})
```

### ES6
```js
import Spinner from 'vue-spinner-component/src/Spinner.vue'

new Vue({
  components: {
    Spinner
  }
})
```
Or: 
```js
Vue.component('spinner', require('vue-spinner-component/src/Spinner.vue'));
```

## Local setup

```
npm install
npm run dev
```

You can customize the color, size, depth, rotation, speed with setting the props. All props have default value.

## License

 vue-spinner-component is licensed under [The MIT License](LICENSE).
