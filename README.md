# ocaml-clean-compile

Compile OCaml code without leaving behind temporary files.

## Overview

The OCaml compiler often generates intermediate files during compilation, which developers must clean up manually.  
This project provides two lightweight shell scripts — `ocaml-bin` and `ocaml-js` — that compile OCaml code in a system temporary directory and automatically remove all intermediate files once the build is complete.

## Features

- **Clean builds**: No leftover `.cmi`, `.cmo`, or other temporary artifacts.
- **Two targets**:
  - `ocaml-bin` → build native executables
  - `ocaml-js` → build JavaScript via `js_of_ocaml`
- **Simple usage**: Just pass your source files; the scripts handle the rest.

## Requirements

### Native Executable (`ocaml-bin`)

- OCaml `4.14.4+` (recommended)
- `opam`

### JavaScript (`ocaml-js`)

In addition to the native requirements:

- `js_of_ocaml`
- `js_of_ocaml-ppx`
- `ocamlfind`

## Usage

### Native Executable

```shell
$ ocaml-bin lib1.ml lib2.ml lib3.ml main.ml
```

### JavaScript

```shell
$ ocaml-js lib1.ml lib2.ml lib3.ml main.ml
```

## Non-Goal

This project does not aim to replace `dune`.

`dune` remains the recommended build system for managing complex OCaml projects.  
ocaml-clean-compile is intended only as a lightweight helper for quick compilation without clutter.

## License

MIT License (c) 2026 ByteBard
