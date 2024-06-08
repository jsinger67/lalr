<!-- markdownlint-disable first-line-h1 -->

[![Rust](https://github.com/jsinger67/lalry/actions/workflows/rust.yml/badge.svg)](https://github.com/jsinger67/lalry/actions/workflows/rust.yml)
[![Docs.rs](https://docs.rs/lalry/badge.svg)](https://docs.rs/lalry)
[![Crates.io](https://img.shields.io/crates/v/lalry.svg)](https://crates.io/crates/lalry)

<!-- markdownlint-enable first-line-h1 -->


# `lalry` - a library for creating LALR(1) parsers from context-free grammars

This is a fork of the great [lalr](https://github.com/goffrie/lalr) crate, a library for
creating LALR(1) parsers from context-free grammars.

## Additions to `lalr`

To make the generation of parse tables more flexible `lalry` adds a way to control this process.
The trait `Config` is used for this and a custom implementation can be provided to deviate from the
default.
To keep the default behavior as in previous versions the user can use the `DefaultConfig` structure
that provides the implementation of the standard behavior.

## Properties of `lalry`

`lalry`, although not the main goal, is functionally fully compatible with it's ancestor `lalr`.
It can be used as drop-in replacement with only minor adaptions.

All you need to do is to create a `DefaultConfig` and hand it over to the call to `lalr1`:

```rust
let config = DefaultConfig::new();
let parse_table = grammar.lalr1(&config).unwrap();
```

By using a default configuration you get the exact same functionality as if you had called

```rust
let parse_table = grammar.lalr1(|_, _| true, |_, _| 0).unwrap();
```

with `lalr` style API.
