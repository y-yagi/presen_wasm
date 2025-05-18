# `ruby_wasm` gem

* Rubyのコード、GemfileをCRubyランタイムと合わせて1つのWasmバイナリを生成するためのgem
* C拡張を使っているgemや、何か独自のRubyスクリプトを含んだWasmバイナリが必要な場合、このgemを使って簡単に作成する事が出来る
* このgemには、`rbwasm`というCLIが提供されており、そのCLIでWasmバイナリを生成出来る
* `rbwasm`は、ビルド対象のディレクトリにGemfileがあれば、そこから使用しているgemをインストールし、そのgemも合わせてWasmバイナリにしてくれる
