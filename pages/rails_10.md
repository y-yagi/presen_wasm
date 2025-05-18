# wasmify:pwa

* `bin/rails wasmify:pwa`
* WasmifyされたRailsアプリケーションで使用するService Workerのセットアップを行う
* このService Workerは、DBのセットアップや、HTTPリクエストのサーブ処理等を行う
  * Service Workerのソースは[これ](https://github.com/palkan/wasmify-rails/blob/main/lib/generators/wasmify/pwa/templates/pwa/rails.sw.js)