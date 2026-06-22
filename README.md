# ocaml-clean-compile

Compile OCaml code without leaving behind temporary files.

## Overview

The OCaml compiler often generates intermediate files during compilation, which developers must clean up manually.  
This project provides two lightweight shell scripts — `ocaml-bin` and `ocaml-js` — that compile OCaml code in a system temporary directory and automatically remove all intermediate files once the build is complete.

## Features

- **Clean builds**: Produces native executables without leaving behind `.cmi`, `.cmo`, or other temporary artifacts.
- **Multiple targets**:
  - `ocaml-std` → build with the OCaml standard library only
  - `ocaml-core` → build with Jane Street’s Base, Stdio, and Core libraries
  - `ocaml-js` → build JavaScript output via `js_of_ocaml`
- **Simple usage**: Just provide your source files — the scripts take care of the rest.

## Requirements

### Native Executable (`ocaml-std`)

- OCaml `4.14.4+` (recommended)
- `opam`

### Jane Street Enhanced Executable (`ocaml-core`)

Includes the native requirements, plus:

- `base`
- `stdio`
- `core`
- `ocamlfind`

In the updated ocaml-clean-compile, `ocaml-core` is simply a thin wrapper around `ocaml-std`.  
If you need to include additional packages, use the following command instead:

```shell
$ ocaml-std -r requirement.txt lib1.ml ... main.ml
```

Remember to list all dependencies in `requirement.txt` again, including `base`, `stdio`, `core`, and any other required packages.

### JavaScript (`ocaml-js`)

Includes the native requirements, plus:

- `js_of_ocaml`
- `js_of_ocaml-ppx`
- `ocamlfind`

## Usage

### Native Executable

```shell
$ ocaml-std lib1.ml lib2.ml lib3.ml main.ml
```

```shell
$ ocaml-core lib1.ml lib2.ml lib3.ml main.ml
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
