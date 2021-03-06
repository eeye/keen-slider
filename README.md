# keen-slider

The HTML touch slider carousel with the most native feeling you will get.

Features:

- only 6.5 KB (2.5 KB gzipped)
- works great and the same, on all devices and browsers (>= IE10)
- no dependencies
- typescript compatible
- examples for the most common SPA's (e.g. react, vue, angular)
- simple API

Demo: https://rcbyr.github.io/keen-slider/

## Getting Started

### Install with npm

```
$ npm install --save keen-slider
```

```html
<html>
  <head>
    <link
      rel="stylesheet"
      href="path/node_modules/keen-slider/dist/keen-slider.min.css"
    />
  </head>
  <body>
    <div id="my-keen-slider" class="keen-slider">
      <div class="keen-slider__track">
        <div class="keen-slider__slide"></div>
        <div class="keen-slider__slide"></div>
        ...
      </div>
    </div>

    <script src="path/node_modules/keen-slider/dist/keen-slider.min.js"></script>
    <script>
      new KeenSlider('#my-keen-slider')
    </script>
  </body>
</html>
```

### Use as ES-Module

```javascript
// optionally import CSS here
import 'keen-slider/dist/keen-slider.min.css'
import KeenSlider from 'keen-slider'

const options_and_events = {
  created: function() {
 console.log('Congratulations! Your slider has ' + this.length + 'items')
  }
  loop: true
}
const slider = new KeenSlider('#my-keen-slider', options_and_events)
```

### Use from CDN

```html
<html>
  <head>
    <link
      rel="stylesheet"
      href="https://cdn.jsdelivr.net/npm/keen-slider@latest/dist/keen-slider.min.css"
    />
  </head>
  <body>
    <div id="my-keen-slider" class="keen-slider">
      <div class="keen-slider__track">
        <div class="keen-slider__slide"></div>
        <div class="keen-slider__slide"></div>
        ...
      </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/keen-slider@latest/dist/keen-slider.min.js"></script>
    <script>
      new KeenSlider('#my-keen-slider')
    </script>
  </body>
</html>
```

## API

### Create Slider

```javascript
var slider = new KeenSlider('#my-slider')
```

- **container** has to be from type HtmlElement or String
  (CSS-Selektor)
- **params** has to be from type object, with [options](#options) and [event hooks](#event-hooks) (optional)

**returns** a slider instance with public [methods](#methods) and [getters](#getters)

### Options

The following options are available.

| Option       | Type     | Default                                 | Description                                 |
| ------------ | -------- | --------------------------------------- | ------------------------------------------- |
| controls     | Boolean  | true                                    | control slider with mouse or touch gestures |
| classSlide   | String   | "keen-slider\_\_slide"                  | necessary class name for a slide            |
| classTrack   | String   | "keen-slider\_\_track"                  | necessary class name for the track          |
| initialSlide | Integer  | 0                                       | initial activate slide                      |
| loop         | Boolean  | true                                    | infinity loop of slides                     |
| moveDuration | Integer  | 500                                     | animation time                              |
| moveEasing   | Function | function (t) { return --t _ t _ t + 1 } | method animation easing                     |

```javascript
var options = {
  loop: false,
  initialSlide: 2,
}
var slider = new KeenSlider('#my-slider', options)
```

### Event hooks

The following event hooks are available.

| Event   | Params | Description                                   |
| ------- | ------ | --------------------------------------------- |
| changed | slide  | will be triggered after the slide has changed |
| created | -      | will be triggered after initialization        |

Example:

```javascript
var options = {
  changed: function(slide) {
    console.log('Slide ' + slide + ' of ' + this.length)
  },
}
var slider = new KeenSlider('#my-slider', options)
```

### Getters

The following getters are available on a slider instance.

| Getter | Description       |
| ------ | ----------------- |
| length | number of slides  |
| slide  | get current slide |

Example:

```javascript
var slider = new KeenSlider(container, params)
console.log('number of slides:' + slider.length)
```

### Methods

The following methods are available on a slider instance.

| Method            | Arguments                                        | Description                                                  |
| ----------------- | ------------------------------------------------ | ------------------------------------------------------------ |
| destroy           | -                                                | remove events and helper slides of the loop - refesh() would undo this |
| moveToSlide       | slide(Integer), instant(Boolean, Default: false) | move to given slide - optionally without animation           |
| next              | -                                                | move to next slide                                           |
| prev              | -                                                | move to previous slide                                       |
| refresh           | -                                                | refresh slider - for example when you add/remove slides      |
| refreshLoopSlides | -                                                | refresh loop slides - if slide content was changed           |
| resize            | -                                                | resize slider - internal resize event ignores height changes |

Example:

```javascript
var slider = new KeenSlider(container, params)
setInterval(slider.next, 5000)
```

## Examples

Demo: https://rcbyr.github.io/keen-slider/

If you miss a features to build the slider you need, create an issue and I will try to help you out.
