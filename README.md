# js_with_embedded_wasm

A tool to convert Deno's wasm and js created by [wasm-bindgen](https://github.com/rustwasm/wasm-bindgen) for deno to js with wasm embedded.

## Usage

Suppose you created wasm and js using [wasm-bindgen](https://github.com/rustwasm/wasm-bindgen) by following the steps below.

```sh 
$ cargo build --lib --release --target wasm32-unknown-unknown
$ wasm-bindgen --target deno target/wasm32-unknown-unknown/debug/csrf_wasm.wasm --out-dir ./pkg
$ ls ./pkg
sample.d.ts  sample.js  sample_bg.wasm  sample_bg.wasm.d.ts
```

Use the following command to perform the conversion.  
Please redirect the result.

```sh
$  deno run --allow-read --unstable https://raw.githubusercontent.com/Octo8080/js_with_embedded_wasm/main/cli.ts --wasm-file=./pkg/sample_bg.wasm --js-file=./pkg/sample.js > ./pkg/sample_with_bin.js
```

