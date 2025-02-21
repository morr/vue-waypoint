# VueWaypoint

> trigger functions and events based on the element position on the screen

![Latest Release](https://github.com/scaccogatto/vue-waypoint/workflows/Release/badge.svg)

## Vue2 and Nuxt version

[vue-waypoint for Vue2 repository](https://github.com/scaccogatto/vue-waypoint/tree/vue2)

## Demo

[Simple demo page](https://vue-waypoint.netlify.app/)

Open your browser console and see what's going on while scrolling up and down

## Features

- [x] Vue 3
- [x] No dependencies
- [x] Flexible
- [x] Typescript
- [x] Battle tested
- [x] Customizable
- [x] Solid project (3+ years)

## Getting started

### npm

```bash
npm i vue-waypoint
```

### Vue component

```html
<template>
  <Waypoint @change="onChange">
    slot content
  </Waypoint>
</template>
```

```html
<script lang="ts">
import { defineComponent } from "vue";
import { VueWaypoint } from 'vue-waypoint'

export default defineComponent({
  name: "SomeComponent",
  components: {
    Waypoint
  },
  setup() {
    const onChange = (waypointState) => {
      // Going can be:
      // IN
      // OUT
      console.log(waypointState.going);

      // Direction can be:
      // UP
      // DOWN
      // LEFT
      // RIGHT
      console.log(waypointState.direction);
    }

    return { onChange };
  }
});
</script>
```

## Props

### `active`

- [x] Can use a reactive variable
- [x] Can set `true`/`false` dinamically

Usage:

- Enable the waypoint: `<Waypoint :active="true" />`
- Disable the waypoint: `<Waypoint :active="false" />`

### `options`

- [x] Useful for inner div detection
- [x] Trigger `change` event a portion of the element is completely on screen
- [x] Is an [official IntersectionObserverInit implementation](https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver/IntersectionObserver)

Usage:

- Set a custom `IntersectionObserver` options: `<Waypoint :options="options" />`
- Read what you can do with `options`: [IntersectionObserverInit docs](https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver/IntersectionObserver)

Options example:

```js
const options: IntersectionObserverInit = {
  root: document,
  rootMargin: '0px 0px 0px 0px',
  threshold: [0.25, 0.75]
};
```

### `tag`

- [x] Set your preferred tag for the element
- [x] Defaults to `div`

- Waypoint as div: `<Waypoint :tag="'div'" /> --> renders --> <div></div>`
- Waypoint as span: `<Waypoint :tag="'span'" /> --> renders --> <span></span>`
- Waypoint as p: `<Waypoint :tag="'p'" /> --> renders --> <p></p>`

## Events

### `change`

Emitted every time the waypoint detects a change.

```html
<template>
  <Waypoint @change="onChange" />
</template>
```

```js
const changeFunction = (waypointState) => {..}
```

```js
WaypointState {
  el: Element,
  going: 'IN' | 'OUT';
  direction: 'UP' | 'DOWN' | 'LEFT' | 'RIGHT';
};
```

## Development

1. Fork the repository
2. Run the project (`npm i && npm run serve`)
3. Follow [Conventional Commits spec](https://www.conventionalcommits.org/en/v1.0.0/) for your commits
4. Open a pull request
