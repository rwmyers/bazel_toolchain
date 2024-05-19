Basic sample of setting up a C++ build toolchain in Bazel. This is based on a [C++ Bazel Tutorial](https://bazel.build/tutorials/ccp-toolchain-config).

The key take-aways are:

 - You need to specify a matching platforms flag in the command line for Bazel to resolve to the toolchain for the same constraint values on the platform. The documentation holds more [information about language specific configuration flags](https://bazel.build/concepts/platforms).
- You have to let the toolchain know where the tools live. In this tutorial there is a simplified version where you access the tools from the system. If you are interested in a more self-contained approach, you can read about workspaces. Your tools could come from a different workspace and you would have to make their files available to the `cc_toolchain` with target dependencies on attributes, such as `compiler_files`. The `tool_paths` would need to be changed as well.
- You can create features to customize which flags should be passed to different actions, be it linking or any other type of action.

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
