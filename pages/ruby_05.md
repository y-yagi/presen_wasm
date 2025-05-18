# npm-packages

* npm packagesをCDN経由で使用するのが一番簡単な使用法
* https://codepen.io/y-yagi/pen/NPPQLzr

```html
<html>
  <script src="https://cdn.jsdelivr.net/npm/@ruby/3.4-wasm-wasi@2.7.1/dist/browser.script.iife.js"></script>
  <script type="text/ruby">
    require "js"
    JS.global[:document].write "Hello World from Ruby #{RUBY_VERSION}"
  </script>
</html>
```
