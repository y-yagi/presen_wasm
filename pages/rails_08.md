# wasmify:build:core

* Wasmで動作しないライブラリは事前にビルドの対象から除外する必要がある
  * `config/wasmify.yml`に指定出来る
  * デフォルトで、bigdecimal、psych、dateなどが指定されている
  * https://github.com/y-yagi/rails_wasmify_blog/blob/main/config/wasmify.yml
