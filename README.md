## docker-cross

Use Docker for cross-compilation with
[`crosstool-ng`](https://github.com/crosstool-ng/crosstool-ng)
toolchains.

The current main focus is on reliable build environments for kernel
development and similarly low-level tasks.

### Supported Targets

Since toolchain builds take a while, targets will be added on an
as-needed basis. GDB will not be enabled in most cases since debugging
will most likely be done from a host machine. Adding a target is
fairly straightforward, and it mostly consists of generating a working
`crosstool-ng` configuration.

* `i686-unknown-elf`

Bare-metal targets do not currently support C++ since `crosstool-ng`
seems to have trouble with a freestanding `libstdc++`, but fixes are
welcome.
