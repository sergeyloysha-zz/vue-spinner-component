VueJS Spinner Component

## [Live demo](http://sergeyloysha.github.io/vue-spinner-component/)

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

## Usage

```html
<spinner :status="spinnerStatus" :color="spinnerColor" :size="spinnerSize" :depth="spinnerDepth" :clockwise="spinnerClockwise" :speed="spinnerSpeed"></spinner>
```

You can customize the color, size, depth, clockwise, speed with setting the props. All props have default value. You can control the spinner show/hidden with setting the status prop.

## License

 vue-spinner-component is licensed under [The MIT License](LICENSE).
