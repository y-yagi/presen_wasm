# wasmify:build:core

* ビルド後、`bin/rails wasmify:build:core:verify`を実行してRailsバージョンが表示されれば出ればビルドOK
* verifyでは、Wasmのランタイムとして、[bytecodealliance/wasmtime](https://github.com/bytecodealliance/wasmtime)を使用している
  * Wasmtimeがインストールされてないとエラーになるよ
  * Wasmtimeでは`js`に関する処理はエラーになるので`js` gemは除外していると思われる
