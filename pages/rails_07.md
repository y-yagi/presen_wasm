# wasmify:build:core

* Wasmで動作しないライブラリは事前にビルドの対象から除外する必要がある
  * `config/wasmify.yml`に指定出来る
  * デフォルトで、bigdecimal、psych、dateなどが指定されている
* C拡張を使用しているgemを追加する度、Rubyのソースコードからの再ビルドが必要
  * なお、これはWASI 0.1の場合。WASI 0.2になればRubyのビルドはいらなくなるはず。