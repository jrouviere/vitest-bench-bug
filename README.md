# vitest-bench-bug

With vitest 0.31.1:
```sh
$ npm install -D vitest@0.31.1 && npx vitest bench --watch false
[...]
 RUN  v0.31.1 /Users/jrouviere/dev/vitest-bench

 ✓ test.bench.js (1) 2546ms
     name                        hz     min     max    mean     p75     p99    p995    p999     rme  samples
   · basic benchmark  13,837,579.79  0.0000  0.7054  0.0001  0.0001  0.0001  0.0001  0.0002  ±0.47%  6918790   fastest
```

With vitest 0.31.2:
```sh
$ npm install -D vitest@0.31.2 && npx vitest bench --watch false
[...]
 RUN  v0.31.2 /Users/jrouviere/dev/vitest-bench

 · test.bench.js (1)
(node:20706) PromiseRejectionHandledWarning: Promise rejection was handled asynchronously (rejection id: 2)

[...]
DataCloneError: () => {
  var n;
  return typeof ((n = globalThis.process) == null ? void 0 : n.hrtime) == "function" ? P(Numbe...<omitted>...
} could not be cloned.
 ❯ new DOMException node:internal/per_context/domexception:53:5
 ❯ post node_modules/vitest/dist/worker.js:48:16
 ❯ node_modules/vitest/dist/vendor-index.5037f2c0.js:132:11
 ❯ sendCall node_modules/vitest/dist/vendor-index.5037f2c0.js:129:16
 ❯ node_modules/vitest/dist/vendor-rpc.4d3d7a54.js:50:18
```