# Wasmランタイム

* Wasmバイナリは仮想命令セットなので、その命令セットを読み取って実行する為のランタイムが必要
  * Java VMなどと同じ
  * ブラウザでは、V8などにWasmランタイムが実装されている
* V8以外にも、[bytecodealliance/wasmtime](https://github.com/bytecodealliance/wasmtime)や、[wasmerio/wasmer](https://github.com/wasmerio/wasmer)などのWasmランタイムがある
  * [udzura/wardite](https://github.com/udzura/wardite)もそうですね
  * 参考：[Running ruby\.wasm on Pure Ruby Wasm Runtime](https://udzura.jp/slides/2025/rubykaigi/#1)
