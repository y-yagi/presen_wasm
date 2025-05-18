# WASI Preview 2

* WASIの最新バージョンは、「WASI Preview 2(WASI 0.2 とも呼ばれている)
* WASI Preview 1を刷新して新たにコンポーネントモデルとそのためのインターフェイスであるWIT(Wasm Interface Type)をベースに開発されている
  * [WebAssembly/wasi-filesystem](https://github.com/WebAssembly/wasi-filesystem)や[WebAssembly/wasi-sockets](https://github.com/WebAssembly/wasi-sockets)など、色々増えた
* コンポーネントモデルは従来のWasmとバイナリの定義が違うので、コンポーネントモデルを使いたい場合、Wasmランタイムがコンポーネントモデルをサポートしている必要がある
