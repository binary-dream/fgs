---
sidebar_position: 1
---

# FGS Introduction

FGS stands for Flutter Glue Style and is composed by a set of patterns and tools to facilitade build flutter app, packages etc.

## Packages Used

Glue on FGS represents a set of packages used by apps using the FGS style:

TODO: Set fgs_utils_v1 path on Github.

```yaml
dependencies:
  flutter_bloc: ^8.1.2
  freezed_annotation: ^2.2.0
  freezed: ^2.3.2
  get_it: ^7.2.0
  injectable: ^2.1.1
  fgs_utils_v1:
    path: /Users/marco/Organizations/BinaryDream/fgs_utils_v1

dev_dependencies:
  build_runner: ^2.3.3
  injectable_generator: ^2.1.5
```

## FGS Architecture

You can find more about the architecture using FGS style [here](/docs/category/fgs-architecture).

## FGS Utils

FGS Utils is a library containing some code shared between apps using FGS style.
You can find the code of this library here: [https://github.com/binary-dream/fgs_utils_v1](https://github.com/binary-dream/fgs_utils_v1).

## FGS Generator

FGS Generator is a [Yeoman](https://yeoman.io/) code generator tool with commands to generate code boilerplate on FGS style in a fast and easy way.
You can found the generator in this repo: [https://github.com/binary-dream/generator-fgs](https://github.com/binary-dream/generator-fgs).