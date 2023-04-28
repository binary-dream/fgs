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

## Delete the .vscode/launch.json

This file will just generate confusion, because we always need to setup the firebase files before running the app. Instead of using the vscode launcher, just use the commands in the Makefile.

## Create the firebase projects and setup them

* **Production**: fgs-example-v1-prod
* **Staging**: fgs-example-v1-stg
* **Development**: fgs-example-v1-dev

[https://codewithandrea.com/articles/flutter-flavors-for-firebase-apps/](https://codewithandrea.com/articles/flutter-flavors-for-firebase-apps/).

It will be necessary change the generated files (firebase_app_id_file.json, GoogleService-Info.plist and google-services.json) location. Save the files for each flavor and copy them to the default place before running the flutter app. Look in the Makefile the commands 'prepare-firebase-files-dev', 'prepare-firebase-files-stg', 'prepare-firebase-files-prod' to know where to save the generated files for each flavor.

Next, is an example of the commands to configure the firebase with the flutterfire cli for each environment:

### Development

```bash
flutterfire config \
  --project=e-comm-app-backbone-v1-dev \
  --ios-bundle-id=tech.binarydream.e-commerce-app-backbone-v1.dev \
  --macos-bundle-id=tech.binarydream.e-commerce-app-backbone-v1.dev \
  --android-package-name=tech.binarydream.e_commerce_app_backbone_v1.dev \
  --out=lib/firebase_options_development.dart
```

### Staging

```bash
flutterfire config \
  --project=e-comm-app-backbone-v1-stg \
  --ios-bundle-id=tech.binarydream.e-commerce-app-backbone-v1.stg \
  --macos-bundle-id=tech.binarydream.e-commerce-app-backbone-v1.stg \
  --android-package-name=tech.binarydream.e_commerce_app_backbone_v1.stg \
  --out=lib/firebase_options_staging.dart
```

### Production

```bash
flutterfire config \
  --project=e-comm-app-backbone-v1-prod \
  --ios-bundle-id=tech.binarydream.e-commerce-app-backbone-v1 \
  --macos-bundle-id=tech.binarydream.e-commerce-app-backbone-v1 \
  --android-package-name=tech.binarydream.e_commerce_app_backbone_v1 \
  --out=lib/firebase_options_production.dart
```

Add the default google-services.json to the .gitignore of the android:

```
app/google-services.json
```

Add the default firebase_app_id_file.json and GoogleService-Info.plist to .gitignore of the ios:

```
Runner/GoogleService-Info.plist
firebase_app_id_file.json
```

## Configure some files on the project

Configure the main's and bootstrap.dart files based on this project: [https://github.com/binary-dream/e_commerce_app_backbone_v1](https://github.com/binary-dream/e_commerce_app_backbone_v1).
