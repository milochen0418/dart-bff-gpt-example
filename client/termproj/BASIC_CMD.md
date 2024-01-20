# command
- flutter doctor -v 
  - check environment
- flutter emulators  
  - list all emulators you have for iOS/android 
- flutter devices
  - 檢查真機或瀏覽器 (以下舉例)
  - $ flutter devices  
      - Found 2 connected devices:  
      macOS (desktop) • macos  • darwin-arm64   • macOS 13.5 22G74 darwin-arm64
      - Chrome (web)    • chrome • web-javascript • Google Chrome 120.0.6099.234
- flutter emulators --launch <emulator_id>
  - launch your emulator by emulator_id  
- flutter run -d <emulator_id>
  - Run the flutter application on the emulator with <emulator_id>


# Make flutter project from helloworld main.dart single file
$ mv main.dart ./lib
$ touch pubspec.yaml
```yaml
name: termproj
description: A new Flutter project.

publish_to: 'none'

version: 1.0.0+1

environment:
  sdk: '>=3.2.4 <4.0.0'

dependencies:
  flutter:
    sdk: flutter

dev_dependencies:
  flutter_test:
    sdk: flutter

flutter:
  uses-material-design: true

```

$ flutter pub get

