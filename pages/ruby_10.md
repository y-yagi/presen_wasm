# `ruby_wasm` gem

* [kateinoigakukun/wasi-vfs](https://github.com/kateinoigakukun/wasi-vfs)を使用して、Wasmバイナリ上に読み込み専用のVFS(Virtual File System)を含むようにしている
* gemやRubyの標準ライブラリなどはそのVFS上に格納されており、`require`で普通にロード出来る
* READMEにも記載されている通り、WASI Preview1向けライブラリ