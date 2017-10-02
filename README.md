# DocuTAP UI

A DocuTAP UI library built for [Vue.js](https://vuejs.org/) forked from [Vue Material](https://github.com/vuematerial/vue-material)

## Features

* Can be consumed via [DocuTAP Form](https://bitbucket.org/docutap/form) and [DocuTAP Inputs](https://bitbucket.org/docutap/inputs) to avoid common boilerplate

## Installation

Import Roboto and Material Icons from Google CDN:

``` html
<link rel="stylesheet" href="//fonts.googleapis.com/css?family=Roboto:300,400,500,700,400italic">
<link rel="stylesheet" href="//fonts.googleapis.com/icon?family=Material+Icons">
```

## Install

```bash
npm install --save git+ssh://git@bitbucket.org/docutap/ui.git#4ef21b4
```

When updating the commit-ish from Bitbucket make sure to source from the [`dist` branch](https://bitbucket.org/docutap/ui/branch/dist).

Import Vue and DocuTAP UI in your code:

``` javascript
import Vue from 'vue'
import DocutapUi from '@docutap/ui'
import '@docutap/ui/dist/ui.css'
```

## Usage

Enable DocuTAP UI in your application using ```Vue.use()```. You can always enable individual components:

``` javascript
Vue.use(DocutapUi)

// OR

Vue.use(DocutapUI.MdCore) // Required to boot DocuTAP UI
Vue.use(DocutapUI.MdButton)
Vue.use(DocutapUI.MdIcon)
Vue.use(DocutapUI.MdSidenav)
Vue.use(DocutapUI.MdToolbar)
```