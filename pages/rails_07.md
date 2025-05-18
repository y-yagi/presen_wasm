# wasmify:build:core

* 依存しているgem(`js` gem以外)を含んだ状態でRubyのWasmバイナリを生成する
  * Wasmバイナリで使用するgemは`wasm`グループで指定する必要がある
  * 先に説明した、`ruby_wasm` gemを使っている
  * `js` gemを除外しているのは、後述するverifyの都合上
* Rubyのコードのダウンロード+Rubyのビルドはこのタイミングで行われる
