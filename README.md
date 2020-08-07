## Build Setup:

``` bash
# Download repository:
git clone https://github.com/vedees/webpack-template webpack-template

# Go to the app:
cd webpack-template

# Install dependencies:
npm install

# Server with hot reload at http://localhost:8080/
npm run dev

# Output will be at dist/ folder
npm run build
```

## Project Structure:

* `src/index.html` - main app HTML
* `src/assets/scss` - put custom app SCSS styles here. Don't forget to import them in `index.js`
* `src/assets/css` - the same as above but CSS here. Don't forget to import them in `index.js`
* `src/assets/img` - put images here. Don't forget to use correct path: `assets/img/some.jpg`
* `src/js` - put custom app scripts here
* `src/index.js` - main app file where you include/import all required libs and init app
* `src/components` - folder with custom `.vue` components
* `src/store` - app store for vue
* `static/` - folder with extra static assets that will be copied into output folder

## Import only SASS or CSS libs:
1. Install libs
2. Go to `/assets/scss/utils/libs.scss`
3. Import libs in node modules
``` scss
// Sass librarys example:
@import '../../node_modules/spinners/stylesheets/spinners';
// CSS librarys example:
@import '../../node_modules/flickity/dist/flickity.css';
```

## Import js files:
1. Create another js module in `./js/` folder
2. Import modules in `./js/index.js` file
``` js
// another js file for example
import './common.js'
```

## Vue install:
Default: **already have**

1. Install vue
``` bash
npm install vue --save
```
2. Init vue `index.js`:
``` js
const app = new Vue({
  el: '#app'
})
```
3. Create div id app
``` html
<div id="app">
  <!-- content -->
</div>
```

## Vuex install:
1. Install vuex
``` bash
npm install vuex --save
```
2. Import Vuex
``` js
import store from './store'
```
3. Create index.js in `./store`
``` js
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)

export default new Vuex.Store({
  // vuex content
})
```

## Add Vue Components:
Create your component in `/components/`

**HTML Usage:**
1. Init component in `index.js`:
``` js
Vue.component('example-component', require('./components/Example.vue').default)
```
2. Any html files:
``` html
 <example-component />
```

**VUE Usage:**
1. import components in .vue:
``` js
import example from '~/components/Example.vue'
```
2. Register component:
``` js
  components: {
    example
  }
```
3. Init in vue component:
``` html
<example />
```

## Add Fonts:

Сhoose one of the ways:
1. Handle menthod,
2. Use mixin;

### Handle:
Add @font-face in `/assets/scss/utils/fonts.scss`:

``` scss
// Example with Helvetica
@font-face {
  font-family: "Helvetica-Base";
  src: url('/assets/fonts/Helvetica/Base/Helvetica-Base.eot'); /* IE9 Compat Modes */
  src: url('/assets/fonts/Helvetica/Base/Helvetica-Base.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
       url('/assets/fonts/Helvetica/Base/Helvetica-Base.woff') format('woff'), /* Pretty Modern Browsers */
       url('/assets/fonts/Helvetica/Base/Helvetica-Base.ttf')  format('truetype'), /* Safari, Android, iOS */
       url('/assets/fonts/Helvetica/Base/Helvetica-Base.svg') format('svg'); /* Legacy iOS */
}
```

Add vars for font in `/assets/scss/utils/vars.scss`:

``` scss
$mySecontFont : 'Helvetica-Base', Arial, sans-serif;
```

### Or with mixin:
By default template support only modern format fonts: .woff, .woffs;

If ypu need svg or more formaths use another mixin in `src/assets/scss/utils/mixin.scss`

**Usage:**
1. Put your font to `src/assets/fonts/FOLDERNAME/FONTNAME`.
FOLLOW: Files Required: 
Example: `.woff, .woffs` formats;
2. Go to `fonts.scss`;
3. Use mixin
Example: `@include font-face("OpenSans", "../fonts/OpenSans/opensans");`,
Example 2: `@include font-face("OpenSans", "../fonts/OpenSans/opensansItalic", 400, italic);`.