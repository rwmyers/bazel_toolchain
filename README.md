Basic sample of setting up a C++ build toolchain in Bazel. This is based on a [C++ Bazel Tutorial](https://bazel.build/tutorials/ccp-toolchain-config).

# Setup
Requires [Bazel](https://bazel.build/install).

It also requires `clang`:
```
sudo apt install clang
```

# Building
For Linux `x84_84`:
```
bazel build //main:hello-world
```

For a fake Android (really using a duplication of the same setup):
```
bazel build //main:hello-world --android_platforms=//toolchain:android_x86_64
```

# Toolchains

## Resolving toolchains

```
bazel build //main:hello-world --toolchain_resolution_debug='@bazel_tools//tools/cpp:toolchain_type'
```
