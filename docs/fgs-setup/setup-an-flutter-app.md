---
sidebar_position: 6
---

# Setup an Flutter App

## Create the project (fgs_example_v1)

```bash
cd ~/Projects;
very_good create flutter_app fgs_example_v1 --org "tech.binarydream"
```

## Setup do FVM

```
cd fgs_example_v1;
fvm use 3.7.11;
```

## Adicione o arquivo .vscode/settings.json

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

## Atualize o .gitignore

```
.fvm/*
!.fvm/fvm_config.json
!.vscode/settings.json
```

## Create the docusaurus site

```bash
npx create-docusaurus@latest docusaurus classic;
```

## Create the makefile

```bash
touch Makefile;
```

The content of the Makefile can be found on [https://github.com/binary-dream/e_commerce_app_backbone_v1/blob/main/Makefile](https://github.com/binary-dream/e_commerce_app_backbone_v1/blob/main/Makefile).

## Create the firebase projects and setup them

* **Production**: fgs-example-v1-prod
* **Staging**: fgs-example-v1-stg
* **Development**: fgs-example-v1-dev

[https://codewithandrea.com/articles/flutter-flavors-for-firebase-apps/](https://codewithandrea.com/articles/flutter-flavors-for-firebase-apps/).
