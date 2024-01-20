# command
- flutter doctor -v 
  - check environment
- flutter emulators  
  - list all emulators you have for iOS/android 
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
  sdk: '>=2.7.0 <3.0.0'

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

