# vue-piece-slider ([Demo](https://dreambo8563.github.io/vue-piece-slider/))

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/9a935d579e394bd38efefd120947288e)](https://app.codacy.com/app/dreambo8563/vue-piece-slider?utm_source=github.com&utm_medium=referral&utm_content=dreambo8563/vue-piece-slider&utm_campaign=Badge_Grade_Dashboard)
[![All Contributors](https://img.shields.io/badge/all_contributors-1-orange.svg?style=flat-square)](#contributors) [![Greenkeeper badge](https://badges.greenkeeper.io/dreambo8563/vue-piece-slider.svg)](https://greenkeeper.io/)
[![Build Status](https://travis-ci.org/dreambo8563/vue-piece-slider.svg?branch=master)](https://travis-ci.org/dreambo8563/vue-piece-slider)
[![Known Vulnerabilities](https://snyk.io/test/github/dreambo8563/vue-piece-slider/badge.svg?targetFile=package.json)](https://snyk.io/test/github/dreambo8563/vue-piece-slider?targetFile=package.json)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![npm](https://img.shields.io/npm/dt/vue-piece-slider.svg?style=flat)

This library is a simplified Vue portal of an awesome [Codrops Article](https://tympanus.net/codrops/2018/02/21/animated-fragment-slideshow/) by [Luis Manuel](https://tympanus.net/codrops/author/luis/) (original [source](https://github.com/lmgonzalves/pieces-slider)).

In this version, just support image type.

![](https://raw.githubusercontent.com/dreambo8563/static-assets/master/vue-piece-slider.png)

## Install

```bash
npm install --save animejs vue-piece-slider
```

## Usage

Check out the [Demo](https://dreambo8563.github.io/vue-piece-slider/) to see it in action.

```js
<template>
  <div class="content" id="app">
    <Slider
      :arrow="true"
      :options="options"
      @click="click"
      class="slider"
      :list="list"
      v-model="activeIndex"
    ></Slider>
  </div>
</template>

<script>
import Slider from "vue-piece-slider"

export default {
  name: "app",
  data() {
    return {
      activeIndex: 0,
      list: [
        "./img/1.jpg",
        "./img/2.jpg",
        "./img/3.jpg",
        "./img/4.jpg",
        "./img/5.jpg"
      ],
      options: {
        angle: 30,
        extraSpacing: { extraX: 1, extraY: -20 },
        piecesWidth: 100,
        ty: 200,
        piecesSpacing: 1,
        animation: {
          duration: 2000,
          easing: "easeOutQuint"
        }
      }
    }
  },
  components: {
    Slider
  },
  methods: {
    click() {
      // eslint-disable-next-line no-console
      console.info("object")
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  .slider {
    width: 400px;
    height: 200px;
  }
}
</style>
```

## Props

| Property | Type            | Default | Description                            |
| :------- | :-------------- | :------ | :------------------------------------- |
| `list`   | Array           | []      | The image list                         |
| `value`  | Number \|String | 0       | The activeIndex                        |
| `arrow`  | Booleans        | true    | if to show the action arrow when hover |

## Options

| Property        | Type          | Default                      | Description                                                                                                                                                               |
| :-------------- | :------------ | :--------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `angle`         | Number        | 45                           | Rotation angle for pieces. All pieces in the same item will have the same rotation angle.                                                                                 |
| `extraSpacing`  | Object        | { extraX: 500, extraY: 200 } | Extra space that should be covered by the pieces. You can set a different value for each axis using an Object like: {extraX: 0, extraY: 0}. This is useful if angle != 0. |
| `piecesWidth`   | Func \|Number | random(50, 200)              | Pieces width.                                                                                                                                                             |
| `piecesSpacing` | Func \|Number | 5                            | Separation among pieces.                                                                                                                                                  |

more params please follow the [package of Piece](https://github.com/lmgonzalves/pieces)

## Credits

- [Pieces](https://github.com/lmgonzalves/pieces) by Luis Manuel
- Images by [Unsplash.com](https://unsplash.com/)
- [anime.js](http://anime-js.com/) by Julian Garnier

## Contributors

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
<table><tr><td align="center"><a href="https://dreambo8563.github.io/"><img src="https://avatars2.githubusercontent.com/u/6948318?v=4" width="100px;" alt="Vincent Guo"/><br /><sub><b>Vincent Guo</b></sub></a><br /><a href="https://github.com/dreambo8563/vue-piece-slider/commits?author=dreambo8563" title="Code">💻</a> <a href="https://github.com/dreambo8563/vue-piece-slider/commits?author=dreambo8563" title="Documentation">📖</a> <a href="#infra-dreambo8563" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a></td></tr></table>

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!
