# A library for customizable vue components

## Demo
[demo](https://gwi-vue-components.gwildu.me/)

## Install

```bash
npm install gwi-vue-components
```

## Usage

```html
<script>
  import GwiCard from 'gwi-vue-component/GwiCard/index.vue'
</script>
```

## Theming

It is possible to theme components and also the global stylings and mixins. The first setup is a bit ugly but from then on it should be straight forward and offer you a very flexible way to do advanced themes.

As a first start copy the template folder from this package `./theme/theme_custom/` to your root directory. Your folder structure should look like this:
```
├ theme_custom
  ├ attributes
    ├ common
      └ index.scss
    ├ components
      ├ <component1>.scss
      ├ <component2>.scss
      ├ ...
    └ index.scss
  └ mixins
    ├ <mixins1>.scss
    ├ <mixins2>.scss
    ├ ...
```

(code for the demo-page: https://github.com/gwildu/gwi-vue-component-demo)

Tested with:

<img alt="browserstack logo" src="https://raw.githubusercontent.com/gwildu/gwi-vue-components/master/media/browserstack-logo.svg?sanitize=true" height="30" />
