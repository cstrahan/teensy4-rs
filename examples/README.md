# `teensy4-bsp` Examples

This directory contains examples that run on your Teensy 4.0 or Teensy 4.1. It
separates examples based on their dependencies:

- The examples prefixed with `rtic_*` demonstrate the [RTIC] framework
- The examples prefixed with `blocking_*` demonstrate a basic `no_main`
  application that uses blocking APIs.

[RTIC]: https://rtic.rs

To understand what each example should do, see the example's documentation at
the top of the file.

## Build and run examples

Make sure you have all of the build dependencies described in the [top-level
README](../README.md#dependencies).

If you have the `teensy_loader_cli` command-line loader installed, you may use
`cargo run` to automatically build an example, convert the program, then call
the loader to run it on hardware. The example below will build and flash the LED
example:

```
cargo run --release --example blocking_led --target thumbv7em-none-eabihf
```

If you don't have the command-line loader installed, follow these steps to build
all examples, then program an example of interest.

Build all of the BSP examples for the MCU. When building all examples, enable
all features:

```
cargo build --release --examples --target thumbv7em-none-eabihf
```

Convert your example of interest to a HEX file. For instance, to convert the
`led` example, run

```
rust-objcopy -O ihex target/thumbv7em-none-eabihf/release/examples/blocking_led blocking_led.hex
```

Finally, load the HEX file onto your board. 

## More examples

For even more hardware examples, check out the examples in [the `imxrt-hal`
project](https://github.com/imxrt-rs/imxrt-hal). Nearly all of these examples
run on a Teensy 4, and they may demonstrate advanced driver features.

Note that the `imxrt-hal` project may have a different workflow for building
and flashing examples. Consult the project documentation to understand how
the workflows differ.
