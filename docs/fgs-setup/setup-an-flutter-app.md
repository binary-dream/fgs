---
sidebar_position: 7
---

# Setup an Flutter App

## Create the project (fgs_example)

```bash
cd ~/Projects;
very_good create flutter_app fgs_example --org "tech.binarydream"
```

## Setup do FVM

```
cd fgs_example;
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
  "java.configuration.updateBuildConfiguration": "disabled",
  "files.exclude": {
    "**/*.mocks.dart": true,
    "**/*.freezed.dart": true,
    "**/*.g.dart": true
  },
}
```

## Atualize o .gitignore

```
# Miscellaneous
*.class
*.lock
*.log
*.pyc
*.swp
.DS_Store
.atom/
.buildlog/
.history
.svn/

# IntelliJ related
*.iml
*.ipr
*.iws
.idea/*

# Visual Studio Code related
.classpath
.project
.settings/
.vscode/*

# Flutter repo-specific
/bin/cache/
/bin/mingit/
/dev/benchmarks/mega_gallery/
/dev/bots/.recipe_deps
/dev/bots/android_tools/
/dev/docs/doc/
/dev/docs/flutter.docs.zip
/dev/docs/lib/
/dev/docs/pubspec.yaml
/dev/integration_tests/**/xcuserdata
/dev/integration_tests/**/Pods
/packages/flutter/coverage/
version

# packages file containing multi-root paths
.packages.generated

# Flutter/Dart/Pub related
**/doc/api/
**/ios/Flutter/.last_build_id
.dart_tool/
.flutter-plugins
.flutter-plugins-dependencies
.packages
.pub-cache/
.pub/
build/
flutter_*.png
linked_*.ds
unlinked.ds
unlinked_spec.ds

# Android related
**/android/**/gradle-wrapper.jar
**/android/.gradle
**/android/captures/
**/android/gradlew
**/android/gradlew.bat
**/android/local.properties
**/android/**/GeneratedPluginRegistrant.java
**/android/key.properties
**/android/.idea/
*.jks

# iOS/XCode related
**/ios/**/*.mode1v3
**/ios/**/*.mode2v3
**/ios/**/*.moved-aside
**/ios/**/*.pbxuser
**/ios/**/*.perspectivev3
**/ios/**/*sync/
**/ios/**/.sconsign.dblite
**/ios/**/.tags*
**/ios/**/.vagrant/
**/ios/**/DerivedData/
**/ios/**/Icon?
**/ios/**/Pods/
**/ios/**/.symlinks/
**/ios/**/profile
**/ios/**/xcuserdata
**/ios/.generated/
**/ios/Flutter/App.framework
**/ios/Flutter/Flutter.framework
**/ios/Flutter/Flutter.podspec
**/ios/Flutter/Generated.xcconfig
**/ios/Flutter/app.flx
**/ios/Flutter/app.zip
**/ios/Flutter/.last_build_id
**/ios/Flutter/flutter_assets/
**/ios/Flutter/flutter_export_environment.sh
**/ios/ServiceDefinitions.json
**/ios/Runner/GeneratedPluginRegistrant.*

# Coverage
coverage/

# Submodules
!pubspec.lock
packages/**/pubspec.lock

# Web related
lib/generated_plugin_registrant.dart

# Symbolication related
app.*.symbols

# Obfuscation related
app.*.map.json

# Exceptions to the above rules.
!**/ios/**/default.mode1v3
!**/ios/**/default.mode2v3
!**/ios/**/default.pbxuser
!**/ios/**/default.perspectivev3
!/packages/flutter_tools/test/data/dart_dependencies_test/**/.packages
!/dev/ci/**/Gemfile.lock
!.vscode/extensions.json
!.vscode/launch.json
!.idea/codeStyles/
!.idea/dictionaries/
!.idea/runConfigurations/

.fvm/*
!.fvm/fvm_config.json
!.vscode/settings.json
lib/l10n/untranslated_messages.json

**/*.mocks.dart
**/*.freezed.dart
**/*.g.dart
```

## Create the docusaurus site

```bash
npx create-docusaurus@latest docusaurus classic;
```

## Create the makefile

```bash
touch Makefile;
```

The content of the Makefile can be found on [https://github.com/binary-dream/e_commerce_app_backbone/blob/main/Makefile](https://github.com/binary-dream/e_commerce_app_backbone/blob/main/Makefile).

## Create the scripts directory with his files

[https://github.com/binary-dream/e_commerce_app_backbone/tree/main/scripts](https://github.com/binary-dream/e_commerce_app_backbone/tree/main/scripts)

## Delete the .vscode/launch.json

This file will just generate confusion, because we always need to setup the firebase files before running the app. Instead of using the vscode launcher, just use the commands in the Makefile.

## Create the firebase projects and setup them

* **Development**: fgs-example-dev
* **Staging**: fgs-example-stg
* **Production**: fgs-example-prod

[https://codewithandrea.com/articles/flutter-flavors-for-firebase-apps/](https://codewithandrea.com/articles/flutter-flavors-for-firebase-apps/).

It will be necessary change the generated files (firebase_app_id_file.json, GoogleService-Info.plist and google-services.json) location. Save the files for each flavor and copy them to the default place before running the flutter app. Look in the Makefile the commands 'prepare-firebase-files-dev', 'prepare-firebase-files-stg', 'prepare-firebase-files-prod' to know where to save the generated files for each flavor.

Next, is an example of the commands to configure the firebase with the flutterfire cli for each environment:

### Development

```bash
flutterfire config \
  --project=e-comm-app-backbone-dev \
  --ios-bundle-id=tech.binarydream.e-commerce-app-backbone.dev \
  --macos-bundle-id=tech.binarydream.e-commerce-app-backbone.dev \
  --android-package-name=tech.binarydream.e_commerce_app_backbone.dev \
  --out=lib/firebase_options_development.dart
```

### Staging

```bash
flutterfire config \
  --project=e-comm-app-backbone-stg \
  --ios-bundle-id=tech.binarydream.e-commerce-app-backbone.stg \
  --macos-bundle-id=tech.binarydream.e-commerce-app-backbone.stg \
  --android-package-name=tech.binarydream.e_commerce_app_backbone.stg \
  --out=lib/firebase_options_staging.dart
```

### Production

```bash
flutterfire config \
  --project=e-comm-app-backbone-prod \
  --ios-bundle-id=tech.binarydream.e-commerce-app-backbone \
  --macos-bundle-id=tech.binarydream.e-commerce-app-backbone \
  --android-package-name=tech.binarydream.e_commerce_app_backbone \
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

Configure the main's, di_container and bootstrap.dart files based on this project: [https://github.com/binary-dream/e_commerce_app_backbone](https://github.com/binary-dream/e_commerce_app_backbone).
