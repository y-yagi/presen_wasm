# wasmify:pack:core

* アプリ全体を1つのWasmバイナリにまとめる
  * `assets`や`config.ru`、`Rakefile`などのファイルを含んだバイナリを生成する
    * assetsのコンパイルはこのコマンド内で行われる
  * `ruby_wasm`と同様に、[kateinoigakukun/wasi-vfs](https://github.com/kateinoigakukun/wasi-vfs)を使用して、Wasmバイナリ上のVFSにファイルを格納している
* ビルド後、`bin/rails wasmify:pack:core:verify`を実行してエラーにならなければOK