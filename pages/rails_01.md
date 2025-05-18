# RailsをWasm

* [palkan/wasmify-rails/](https://github.com/palkan/wasmify-rails/)というRailsアプリケーションをWasmバイナリにするgemがある
  * 先行事例として、[PoC: Run Mastodon server on browser](https://github.com/kateinoigakukun/mastodon.wasm/tree/katei/wasmify) がある
  * wasmify-railsでは、上記Mastodnの対応のコードが使われている箇所がある
* 試してみたい方は、[WebAssembly での Ruby on Rails、フルスタックのブラウザ内開発  \|  web\.dev](https://web.dev/blog/ruby-on-rails-on-webassembly?hl=ja) を見ながらやるのがおすすめです
  * [Ruby 3.4+では動かないはず](https://github.com/palkan/wasmify-rails/issues/7)
