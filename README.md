# simse_bootstrap

The published bootstrap of the [Simse](https://github.com/ciplogic/simse) compiler: the
generated C++ that lets a clean checkout build the compiler with a C++ compiler alone.

`builds/simse_bootstrap.cpp` is the generated amalgamation. It is **generated, never
hand-edited**; the Simse repo's tooling writes it and verifies the fixed point.

## Refresh

From the Simse checkout, with the compiler already built:

```sh
bun build.js --release --no-compile --bootstrap
```

`--bootstrap` writes to this repository's `builds/simse_bootstrap.cpp`. The Simse tools
look for this checkout as `../simse_bootstrap` (a sibling of the Simse repo); point them
elsewhere with `SIMSE_BOOTSTRAP` (the file) or `SIMSE_BOOTSTRAP_REPO` (this checkout).

## Verify

```sh
bun tools/bootstrap.js          # compile the published file, transpile, compare bytes
bun tools/bootstrap.js --quick  # one transpile against the published file
```

Tags and releases record the bootstrap that belongs to a Simse revision.
