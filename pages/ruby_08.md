# `ruby_wasm` gem

* Rubyコード、GemfileをRubyランタイムと合わせてWasmバイナリを生成出来るgem
* このgemには、`rbwasm`というCLIが提供されており、そのCLIでWasmバイナリを生成出来る
* `rbwasm`は、Gemfileがあれば、そこから使用しているgemをインストールし、そのgemも合わせてWasmバイナリにしてくれる