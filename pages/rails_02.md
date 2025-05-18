# wasmify-rails

* Railsアプリケーションを含むWasmバイナリを生成する為のコマンドや、Wasmバイナリで動作しないライブラリの為のモンキーパッチ、ウェブサーバーの為の処理、などを提供している
  * 例えば、NokogiriはWasmバイナリで動かないので、Nokogiriの処理を無効化するパッチ
  * Active StorageをWasmバイナリ上で動作させる為の対応、など
