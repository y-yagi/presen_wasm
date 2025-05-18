# RubyでWasm

* CRuby 3.2からWasmバイナリへのコンパイルがサポート
  * [Ruby meets WebAssembly](https://speakerdeck.com/kateinoigakukun/ruby-meets-webassembly)
* CRubyがWasmバイナリにコンパイル出来るようになったため、そのバイナリを使用してRubyのコードが動く
* Rubyのほぼすべての機能がWasmバイナリで実行可能
  * スレッドは動かない