# ブラウザでWASI

* 先程も記載したとおり、npmで提供されているRubyのWasmバイナリは、WASIをサポートしている
* しかしブラウザは、今のところWASI完全互換ではない
* ブラウザでWASIのインターフェースを使用するためのshimライブラリがあり、JS向けのライブラリではそれを使用している
  * [bjorn3/browser_wasi_shim](https://github.com/bjorn3/browser_wasi_shim)
