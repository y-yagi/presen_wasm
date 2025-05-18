# `js` gem

* RubyからJavaScriptを操作する為のライブラリ
* https://codepen.io/y-yagi/pen/ByyXOOj

```html
<html>
  <script src="https://cdn.jsdelivr.net/npm/@ruby/3.4-wasm-wasi@2.7.1/dist/browser.script.iife.js"></script>
  <script type="text/ruby">
    require "js"

    div = JS.global[:document].createElement("div")
    div[:innerText] = "click me"
    body = JS.global[:document][:body]
    body.appendChild(div)

    div.addEventListener("click") do |event|
      div[:innerText] = "clicked!"
    end
  </script>
</html>
```

* 詳細な使いかたは[cheat_sheet.md](https://github.com/ruby/ruby.wasm/blob/main/docs/cheat_sheet.md)を見てね
