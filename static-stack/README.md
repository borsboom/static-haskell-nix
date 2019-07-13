# Fully statically linked `stack`

This builds a fully statically linked `stack` executable that should work on any 64-bit Linux distribution.

It uses nix to build everything, including `ghc`, against the `musl` libc.

## Building

```
$(nix-build --no-link -A fullBuildScript --argstr stackDir /absolute/path/to/stack/source)
```

We use the `$(nix-build ...)` script approach in order to pin the version of `nix` itself for reproducibility, and because the call to `stack2nix` needs Internet access and thus has to run outside of the nix build sandbox.

If you get an error such as:

> stack2nix: user error (No such package foo-1.2.3.4 in the cabal database. Did you run cabal update?)

then update the `hackageSnapshot` date  in `default.nix` to a date that includes the package and version.

## Binary caches for faster building (optional)

You can use the caches described in the [top-level README](../README.md#binary-caches-for-faster-building-optional) for faster building.

## `stack` binaries

Static `stack` binaries I built this way, for download:

* The [official static stack v2.1.3 release](https://github.com/commercialhaskell/stack/releases/tag/v2.1.3) is built using this
* The [official static stack v2.1.1 release](https://github.com/commercialhaskell/stack/releases/tag/v2.1.1) is built using this
* The [official static stack v1.9.3 release](https://github.com/commercialhaskell/stack/releases/tag/v1.9.3) is built using this
* [stack v1.7.1 for 64-bit Linux](https://github.com/nh2/stack/releases/tag/v1.6.5)
* [stack v1.6.5 for 64-bit Linux](https://github.com/nh2/stack/releases/tag/v1.6.5)
