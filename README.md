Basic sample of setting up a C++ build toolchain in Bazel. This is based on a [C++ Bazel Tutorial](https://bazel.build/tutorials/ccp-toolchain-config).

Requires [Bazel](https://bazel.build/install).

# Building
```
bazel build //main:hello-world
```

# Toolchains

## Resolving toolchains

```
bazel build //main:hello-world --toolchain_resolution_debug='@bazel_tools//tools/cpp:toolchain_type'
```
