# `gimli`

[![](http://meritbadge.herokuapp.com/gimli) ![](https://img.shields.io/crates/d/gimli.svg)](https://crates.io/crates/gimli)
[![](https://docs.rs/gimli/badge.svg)](https://docs.rs/gimli/)
[![Build Status](https://travis-ci.org/gimli-rs/gimli.svg?branch=master)](https://travis-ci.org/gimli-rs/gimli)
[![Coverage Status](https://coveralls.io/repos/github/gimli-rs/gimli/badge.svg?branch=master)](https://coveralls.io/github/gimli-rs/gimli?branch=master)

`gimli` is a blazing fast library for consuming the
[DWARF debugging format](http://dwarfstd.org/).

* **Zero copy:** everything is just a reference to the original input buffer. No
  copies of the input data get made.

* **Lazy:** you can iterate compilation units without parsing their
  contents. Parse only as many debugging information entry (DIE) trees as you
  iterate over. `gimli` also uses `DW_AT_sibling` references to avoid parsing a
  DIE's children to find its next sibling, when possible.

* **Cross-platform:** `gimli` makes no assumptions about what kind of object
  file you're working with. The flipside to that is that it's up to you to
  provide an ELF loader on Linux or Mach-O loader on macOS.

  * Unsure which object file parser to use? Try the cross-platform
  [`object`](https://github.com/gimli-rs/object) crate. See the
  [`examples/`](./examples) directory for usage with `gimli`.

## Install

Add this to your `Cargo.toml`:

```toml
[dependencies]
gimli = "0.19.0"
```

The minimum supported Rust version is 1.32.0.

## Documentation

* [Documentation on docs.rs](https://docs.rs/gimli/)

* Example programs:

  * [A simple `.debug_info` parser](./examples/simple.rs)

  * [A simple `.debug_line` parser](./examples/simple_line.rs)

  * [A `dwarfdump` clone](./examples/dwarfdump.rs)

  * [An `addr2line` clone](https://github.com/gimli-rs/addr2line)

  * [`ddbug`](https://github.com/philipc/ddbug), a utility giving insight into
    code generation by making debugging information readable.

  * [`dwprod`](https://github.com/fitzgen/dwprod), a tiny utility to list the
    compilers used to create each compilation unit within a shared library or
    executable (via `DW_AT_producer`).

  * [`dwarf-validate`](./examples/dwarf-validate.rs), a program to validate the
    integrity of some DWARF and its references between sections and compilation
    units.

## License

Licensed under either of

  * Apache License, Version 2.0 ([`LICENSE-APACHE`](./LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
  * MIT license ([`LICENSE-MIT`](./LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

## Contribution

See [CONTRIBUTING.md](./CONTRIBUTING.md) for hacking.

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
