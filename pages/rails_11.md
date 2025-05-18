# wasmify:pwa

* `wasmify:pwa`で先に説明した、アプリケーションで使用するService Workerのセットアップや、ローカルで検証するためのViteの設定などを生成
* `wasmify:pack`で最終のWasmバイナリを生成
  * `wasmify:build:core`では除外した`js` gemも含んで、再度アプリケーション全体を含むバイナリを生成
