# DocuTAP Vue UI

## Installation

Import Roboto and Material Icons from Google CDN:

``` html
<link rel="stylesheet" href="//fonts.googleapis.com/css?family=Roboto:300,400,500,700,400italic">
<link rel="stylesheet" href="//fonts.googleapis.com/icon?family=Material+Icons">
```

## Private npm install

To install from Bitbucket add this to your package.json:

`"vue-material": "git+https://dt-acarriger@bitbucket.org/dt-acarriger/vue-material.git#967e1efy"`

Import or require Vue and Vue Material in your code:

``` javascript
import Vue from 'vue'
import VueMaterial from 'vue-material'
import 'vue-material/dist/vue-material.css'

// OR

var Vue = require('vue')
var VueMaterial = require('vue-material')
require('vue-material/dist/vue-material.css')
```

## Usage

Enable Vue Material in your application using ```Vue.use()```. You can always enable individual components:

``` javascript
Vue.use(VueMaterial)

// OR

Vue.use(VueMaterial.MdCore) //Required to boot vue material
Vue.use(VueMaterial.MdButton)
Vue.use(VueMaterial.MdIcon)
Vue.use(VueMaterial.MdSidenav)
Vue.use(VueMaterial.MdToolbar)
```
