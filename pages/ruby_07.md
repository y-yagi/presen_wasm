# ブラウザでWASI

* 先程も記載したとおり、npmで提供されているRubyのWasmバイナリは、WASIをサポートしている
* しかしブラウザはWASI互換ではない
* ブラウザでWASIのインターフェースを使用するためのshimライブラリがあり、Rubyではそれを使用している
  * [bjorn3/browser_wasi_shim](https://github.com/bjorn3/browser_wasi_shim)
