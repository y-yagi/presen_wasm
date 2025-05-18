# npm-packages

* プリコンパイル済みのWasmバイナリが、各Rubyバージョン事に提供されている
  * `@ruby/3.2-wasm-wasi`、`@ruby/3.3-wasm-wasi`、`@ruby/3.4-wasm-wasi`
  * 末尾が`wasi`になっているのはWASI Preview 1サポート。
* WASI Preview2をサポートしているのは、今のところRuby headのみ(`@ruby/head-wasm-wasip2`)のもよう
* Emscriptenでコンパイルされたパッケージもあるが、恐らく使用することはないと思うので割愛
