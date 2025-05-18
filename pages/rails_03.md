# wasmify-rails

* Railsの全部の機能は動かない
  * 例えば、非同期ジョブは動作しない(inlineのみ)、メール送信は出来ない、など
* RDBMSは、[SQLite Wasm](https://github.com/sqlite/sqlite-wasm)を使用可能
  * Wasmで使えるPostgreSQL([PGlite](https://pglite.dev/))もあるが、Wasmify Railsとしては今のところ未サポート
  * Wasmで使えるMySQLは無さそう
