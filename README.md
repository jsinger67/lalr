# lalry

This is a fork of the great [lalr](https://github.com/goffrie/lalr) crate, a library for
creating LALR(1) parsers from context-free grammars.

## Additions to 'lalr'

To make the generation of parse tables more flexible we added a way to control this process.
The trait `Config` is used for this and a custom implementation can be provided to deviate from the
default.
To keep the default behavior as in previous versions the user can use the `DefaultConfig` structure
that provides the implementation of the standard behavior.
