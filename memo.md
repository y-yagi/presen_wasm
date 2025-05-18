## Wasm

* WebAssemblyの略称
* W3Cによって標準化されている
* Webブラウザ上で動くバイナリコードの新しいフォーマット(だった)
  * 今はWebブラウザ上に限っていない

## Features

* Language-Independent
  * Rust、Go、C/C++、Zigなど、様々なプログラミング言語からバイナリコードを生成出来る
  * このバイナリファイルはWasmモジュールと呼ばれてる
* Portable
  * Wasmバイナリは特定のプラットフォームに依存していない
  * Wasmのランタイムがあれば、ブラウザ以外(Linuxサーバ等)でもどこでも動く
  * 「Write once, run anywhere」
* Secure
  * Wasmバイナリはサンドボックス内で動作する
  * サンドボックスでは、与えられたホスト関数しか実行できないし、与えられたメモリにしかアクセスできない

## Wasmランタイム

* かつてはWebブラウザしかなかったが、今は[bytecodealliance/wasmtime](https://github.com/bytecodealliance/wasmtime)や、[wasmerio/wasmer](https://github.com/wasmerio/wasmer)などがある
  * [udzura/wardite](https://github.com/udzura/wardite)も
  * 参考：[Running ruby\.wasm on Pure Ruby Wasm Runtime](https://udzura.jp/slides/2025/rubykaigi/#1)
* 上記ライブラリを使用することで、Webブラウザ以外でもWasmバイナリを実行可能

## WASI

* WebAssembly System Interface
* Wasmをブラウザ外で実行するためのインターフェイスを標準化したもの
  * POSIXみたいなもの
* 環境変数を取得する、FileDescriptorに書き込む、などのインターフェースが定義されており、 このインターフェースに従う事で、どの環境でも同じように処理が出来る

## WASI Preview 2

* WASIのv2(WASI 0.2 とも呼ばれている)
* WASI Preview 1を刷新して新たにコンポーネントモデルとそのためのインターフェイスであるWITをベースに開発されている

## ruby.wasm

* https://github.com/ruby/ruby.wasm
* 「ruby.wasm is a collection of WebAssembly ports of the CRuby.」
  * WASI環境の為のnpmライブラリ
  * プリコンパイル済みのWasmバイナリ
  * RubyからJSを操作するためのサポートライブラリ
  * などなどが提供されている

## npmライブラリ

* 各Rubyバージョン毎にバイナリが提供されている
  * @ruby/3.4-wasm-wasi、@ruby/3.3-wasm-wasiなど
* stableバージョンはWASI Preview 1互換で、WASI Preview 2互換のライブラリは、今のところRuby head(@ruby/head-wasm-wasip2)のみ


## デモ

```html
<html>
  <script src="https://cdn.jsdelivr.net/npm/@ruby/3.4-wasm-wasi@2.7.1/dist/browser.script.iife.js"></script>
  <script type="text/ruby">
    require "js"
    JS.global[:document].write "Hello, world!"
  </script>
</html>
```

## ruby.wasm

* 昨年RubyGemsがサポートされた
  * [RubyGems on ruby\.wasm \- Speaker Deck](https://speakerdeck.com/kateinoigakukun/rubygems-on-ruby-dot-wasm)
* (全部ではないが)C拡張で作成されたgemもサポート
* 結果、頑張ればRailsアプリケーションも動くようになった
  * [ruby/ruby.wasm?tab=readme-ov-file](https://github.com/ruby/ruby.wasm?tab=readme-ov-file)


## Wasmify Rails

* [palkan/wasmify-rails](https://github.com/palkan/wasmify-rails)
  * RailsアプリケーションをWasmに変換するためのライブラリ
  * Wasmバイナリを生成する為のコマンドや、Wasmバイナリで動作しないライブラリの為のモンキーパッチ、ウェブサーバーの為の処理、などを提供している

## Wasmify Rails

* Railsの全部の機能が動く状態ではない
  * 例えば、非同期ジョブは今の所動作しない
* RDBMSは、[sqlite/sqlite-wasm](https://github.com/sqlite/sqlite-wasm)を使用可能
  * Wasmで使えるPostgreSQL([PGlite](https://pglite.dev/))もあるが、Wasmify Railsとしては今のところ未サポート

## Wasmify Rails

* Ruby 3.4で動かない気がするがどうだろう
  * [Seems to be a compatibility issue with Ruby 3.4](https://github.com/palkan/wasmify-rails/issues/7)
  * [Error compiling BigDecimal extension](https://github.com/ruby/ruby.wasm/issues/558)

## Wasmify Rails(Step 1)

* `bin/rails wasmify:install`
* wasmify-railsの為の設定ファイルを生成
* wasmify-railsでは、Rails envに"wasm"を使用するようになっており、そのための設定ファイルの追加等も行う

## Wasmify Rails(Step 2)

* `bin/rails wasmify:build:core`
* 依存しているgem(JS関係以外)を含んだ状態でruby.wasmのビルドを行う
* Rubyのコードのダウンロード+Rubyのビルドが行われるのでまあまあ重い

## Wasmify Rails(Step 2)

* Wasmで動作しないライブラリはビルドの対象から除外する必要がある
  * `config/wasmify.yml`に指定出来る
  * デフォルトで、bigdecimal、psych、dateなどが指定されている
* C拡張を使用しているgemを追加すると、再度Rubyのビルドが必要
  * WASI 0.1の場合。WASI 0.2になればRubyのビルドはいらなくなるはず

## Wasmify Rails(Step 2)

* ビルド後、`bin/rails wasmify:build:core:verify`を実行してRailsバージョンが出ればビルドOK
* ビルド時点でWasmバイナリが生成されいてる、verifyでは、Wasmのランタイムとして、[bytecodealliance/wasmtime](https://github.com/bytecodealliance/wasmtime)を使用している
  * wasmtimeがインストールされてないとエラーになるよ

## Wasmify Rails(Step 3)

* `bin/rails wasmify:pack:core`
* アプリ全体を1つのWasmバイナリにまとめる
  * `assets`や`config.ru`、`Rakefile`などのファイルを含んだバイナリを生成する
  * [kateinoigakukun/wasi-vfs](https://github.com/kateinoigakukun/wasi-vfs)を使用している

## Wasmify Rails(Step 3)

* ビルド後、`bin/rails wasmify:pack:core:verify`を実行してエラーにならなければOK

## Wasmify Rails(Step 4)

* `bin/rails wasmify:pwa`
* WasmifyされたRailsアプリケーションで使用するService Workerのセットアップを行う
* このService Workerは、DBのセットアップや、HTTPリクエストのサーブ処理等を行う
  * Service Workerのソースは[これ](https://github.com/palkan/wasmify-rails/blob/main/lib/generators/wasmify/pwa/templates/pwa/rails.sw.js)

## Wasmify Rails(Step 4)

* `bin/rails wasmify:pack
* `bin/rails wasmify:pwa`で生成されたJSファイル等を含んたWasmバイナリを生成
* これで完成

## コンテナ

## showcase

* [ruby/ruby.wasm/wiki/Showcase](https://github.com/ruby/ruby.wasm/wiki/Showcase)
* https://runruby.dev/

## まとめ

* 数多のデバイスで走るWasm

## memo

* https://zenn.dev/shiguredo/articles/duckdb-wasm-dashboard
* [Posts, videos, links · Ruby on Rails on WebAssembly · Vladimir Dementyev](https://writebook-on-wasm.fly.dev/5/ruby-on-rails-on-webassembly/66/posts-videos-links)
* [wasmCloud \- A CNCF Project \| wasmCloud](https://wasmcloud.com/)
* [bytecodealliance/wasm-micro-runtime](https://github.com/bytecodealliance/wasm-micro-runtime)
* [component\-model/design/mvp/Linking\.md at main · WebAssembly/component\-model](https://github.com/WebAssembly/component-model/blob/main/design/mvp/Linking.md)
* [Azure Kubernetes Service \(AKS\) 内で WebAssembly System Interface \(WASI\) ノード プールを作成して WebAssembly \(Wasm\) ワークロードを実行する \(プレビュー\) \- Azure Kubernetes Service \| Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/aks/use-wasi-node-pools)
* [マイクロソフト、OSを介さず仮想化ハイパーバイザ上でWasmを高速起動し実行できる「Hyperlight Wasm」、オープンソースで公開 － Publickey](https://www.publickey1.jp/blog/25/oswasmhyperlight_wasm.html)
* https://webassembly.org/features/
* https://zenn.dev/skanehira/books/writing-wasm-runtime-in-rust/viewer/02_about_wasm
* プラグインシステム
  * https://github.com/zellij-org/zellij
  * [spec/docs/WebAssembly\-in\-Envoy\.md at main · proxy\-wasm/spec](https://github.com/proxy-wasm/spec/blob/main/docs/WebAssembly-in-Envoy.md)

* [bjorn3/browser_wasi_shim](https://github.com/bjorn3/browser_wasi_shim)
* [skryukov/runruby\.dev: A basic playground built with ruby\.wasm](https://github.com/skryukov/runruby.dev)
* [Assembling the Future: crafting the missing pieces of the Ruby on Wasm puzzle by Evil Martians](https://evilmartians.com/events/assembling-the-future-ruby-on-wasm-puzzle-euruko)
* [bjorn3/browser_wasi_shim](https://github.com/bjorn3/browser_wasi_shim)
* [WebAssembly/tool-conventions/blob/main/DynamicLinking.md](https://github.com/WebAssembly/tool-conventions/blob/main/DynamicLinking.md)