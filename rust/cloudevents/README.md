# Rust Events Function

Known Issues:
This is currently using a forked version of cloudevents as the `autocfg` build in `claim` does not work correctly in WASI.

Welcome to your new Rust function project! The boilerplate
[hyper-wasi](https://github.com/WasmEdge/hyper/) web server is in
[`src/main.rs`](./src/main.rs). It's configured to invoke the `handle_event`
function in [`src/handler.rs`](./src/handler.rs) in response to a POST
request containing a valid `CloudEvent`. You should put your desired
behavior inside that `handle` function.

The app will expose three endpoints:

  * `/` Triggers the `handle` function for a POST method
  * `/health/readiness` The endpoint for a readiness health check
  * `/health/liveness` The endpoint for a liveness health check

You may use any of the available [hyper
features](https://hyper.rs/guides/0.14/) to fulfill the requests at those
endpoints.

## Development

To get started you will need the following

1. [install WASMEdge](https://wasmedge.org/book/en/quick_start/install.html)

2. Install `cargo wasi` with `cargo install cargo-wasi`

3. Set `CARGO_TARGET_WASM32_WASI_RUNNER=wasmedge` in your `.profile`.
   Or run `export CARGO_TARGET_WASM32_WASI_RUNNER=wasmedge` in the current console.


Once the setup is complete you should be able to run the following commands successfully
```shell script
cargo wasi build # build your code in debug mode for the wasi target.

cargo wasi build --release # build the optimized version of your *.wasm.

cargo wasi run # execute a binary.

cargo wasi test # run your tests in wasm32-wasi.
or
cargo test --target wasm32-wasi -- --nocapture # If you want more verbose output

cargo wasi bench # run your benchmarks in wasm32-wasi.
```

Once running, the function is available at <http://localhost:8080> and
the health checks are at <http://localhost:8080/health/readiness> and
<http://localhost:8080/health/liveness>. To POST data to the function,
a utility such as `curl` may be used:

```console
curl -v -d '{"name": "Bootsy"}' \
  -H'content-type: application/json' \
  -H'ce-specversion: 1.0' \
  -H'ce-id: 1' \
  -H'ce-source: http://cloudevents.io' \
  -H'ce-type: dev.knative.example' \
  http://localhost:8080
```

## Deployment

### TBD
<!--
Use `func` to containerize your application, publish it to a registry
and deploy it as a Knative Service in your Kubernetes cluster:

```shell script
func deploy --registry=docker.io/<YOUR_ACCOUNT>
```

You can omit the `--registry` option by setting the `FUNC_REGISTRY`
environment variable. And if you forget, you'll be prompted.

The output from a successful deploy should show the URL for the
service, which you can also get via `func info`, e.g.

```console
curl -v -d '{"name": "Bootsy"}' \
  -H'content-type: application/json' \
  -H'ce-specversion: 1.0' \
  -H'ce-id: 1' \
  -H'ce-source: http://cloudevents.io' \
  -H'ce-type: dev.knative.example' \
  $(func info -o url)
```
-->
Have fun!