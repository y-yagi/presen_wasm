# wasmify:build:core

* 依存しているgem(JS関係以外)を含んだ状態でRubyのWasmバイナリを生成する
  * 先に説明した、`ruby_wasm` gemを使ってやっている
* Rubyのコードのダウンロード+Rubyのビルドはこのタイミングで行われる