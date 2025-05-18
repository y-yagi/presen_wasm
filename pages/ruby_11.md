# `ruby_wasm` gem

* C拡張を使用しているgemがある場合、CRubyのコンパイル時にC拡張も合わせてコンパイルする必要がある
* そのため、GemfileにC拡張を使用しているgemを追加すると、CRubyのコンパイルから再度実行が必要
* なお、これはWASI Preview1の場合
* WASI Preview2だと、この問題が解消されるらしい(該当のgemのコンパイル+dynamic load)
  * 詳細は、[RubyGems on ruby\.wasm](https://speakerdeck.com/kateinoigakukun/rubygems-on-ruby-dot-wasm) をみてね
