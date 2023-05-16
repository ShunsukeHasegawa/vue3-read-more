# vue3-read-more
![GitHub](https://img.shields.io/github/license/ShunsukeHasegawa/vue3-read-more)
![npm](https://img.shields.io/npm/v/@lazgram/vue3-read-more)
![npm](https://img.shields.io/npm/dm/@lazgram/vue3-read-more)

vue3-read-more is a simple plugin for vue.js

## Demo & Examples
Check out our [demo page](https://shunsukehasegawa.github.io/vue3-read-more/) to see the product in action!

## Installation
```bash
npm install @lazgram/vue3-read-more --save
```

## Usage
```javascript
import ReadMore from '@lazgram/vue3-read-more'
Vue.use(ReadMore)
```

```javascript
<template>
    <read-more>Example test.</read-more>
</template>
```

## API
#### Arguments

- `rows` - The number of lines displayed in the initial state. The default value is 4.
- `moreText` - The text displayed on "Read more". The default value is "Read More"
- `backgroundColor` - The background color of the page. The default value is #FFF.

## License

This project is licensed under the [MIT License](LICENSE).