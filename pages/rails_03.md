# wasmify-rails

* Railsの全部の機能が動く状態ではない
  * 例えば、非同期ジョブは今の所動作しない
* RDBMSは、[sqlite/sqlite-wasm](https://github.com/sqlite/sqlite-wasm)を使用可能
  * Wasmで使えるPostgreSQL([PGlite](https://pglite.dev/))もあるが、Wasmify Railsとしては今のところ未サポート
  * Wasmで使えるMySQLは無さそう