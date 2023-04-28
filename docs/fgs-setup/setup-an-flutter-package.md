---
sidebar_position: 7
---

# Setup an Flutter Package

## Create the package

```bash
cd ~/Projects;
very_good create flutter_package fgs_example_package_v1;
```

## Create/update .gitignore

```
.vscode
.dart_tool
.fvm/flutter_sdk
.flutter-plugins
.flutter-plugins-dependencies
```

## Setup fvm

```bash
fvm use 3.7.11;
```

## Setup vscode settings

```json
{
  "dart.flutterSdkPath": ".fvm/flutter_sdk",
  "[dart]": {
    "editor.defaultFormatter": "Dart-Code.dart-code",
    "editor.formatOnSave": false,
    "editor.formatOnType": false,
  },
}
```

## Create the docusaurus site

```bash
npx create-docusaurus@latest docusaurus classic;
```

## Create the Makefile

```bash
touch Makefile;
```

The content of the Makefile can be found on [https://github.com/binary-dream/fgs_utils_v1/blob/main/Makefile](https://github.com/binary-dream/fgs_utils_v1/blob/main/Makefile).
