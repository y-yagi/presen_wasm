# wasmify-rails

* サーバはどうしているのかというと、Service Workerを使用している
* ブラウザからリクエストが行われたら、それをService Workerがインターセプトして、独自のhandler(RackHandler)を使用して処理を返している
* [Serivice Workerのコード](https://github.com/palkan/wasmify-rails/blob/main/lib/generators/wasmify/pwa/templates/pwa/rails.sw.js)
* [RackHandlerのコード](https://github.com/palkan/wasmify-rails/blob/main/src/rack.js)
