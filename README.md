# DocuTAP UI [![npm version](https://badge.fury.io/js/%40docutap-api%2Fui.svg)](https://badge.fury.io/js/%40docutap-api%2Fui)

A DocuTAP UI library built for [Vue.js](https://vuejs.org/) forked from [Vue Material](https://github.com/vuematerial/vue-material)

## Features

- Can be consumed via [DocuTAP Form](https://github.com/DocuTAP/form) and [DocuTAP Inputs](https://github.com/DocuTAP/inputs) to avoid common boilerplate

## Installation

Import Roboto and Material Icons from Google CDN:

```html
<link rel="stylesheet" href="//fonts.googleapis.com/css?family=Roboto:300,400,500,700,400italic">
<link rel="stylesheet" href="//fonts.googleapis.com/icon?family=Material+Icons">
```

## Install

```bash
npm install --save @docutap-api/ui
```

Import Vue and DocuTAP UI in your code:

```javascript
import Vue from 'vue';
import DocutapUi from '@docutap-api/ui';
import '@docutap-api/ui/dist/ui.css';
```

## Usage

Enable DocuTAP UI in your application using `Vue.use()`. You can always enable individual components:

```javascript
Vue.use(DocutapUi);

// OR

Vue.use(DocutapUI.MdCore); // Required to boot DocuTAP UI
Vue.use(DocutapUI.MdButton);
Vue.use(DocutapUI.MdIcon);
Vue.use(DocutapUI.MdSidenav);
Vue.use(DocutapUI.MdToolbar);
```
