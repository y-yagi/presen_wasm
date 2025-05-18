# `ruby_wasm` gem

```ruby
# Gemfile

source "https://rubygems.org"

gem "ruby_wasm", "~> 2.7"
gem "rainbow", "~> 3.1"
```

```
$ bundle exec rbwasm build -o ruby.wasm
$ wasmtime run ruby.wasm -W0 -r/bundle/setup -rrainbow -e 'puts Rainbow("this is red").red'
```

※rbwasm buildでCRubyのソースのダウンロード+コンパイルが走ります
