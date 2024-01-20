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





```
 (base) milo@MacBook ~/git/dart-bff-gpt-example/client/termproj (main) $ flutter run -d macOS
Launching lib/main.dart on macOS in debug mode...
Exception: No macOS desktop project configured. See https://docs.flutter.dev/desktop#add-desktop-support-to-an-existing-flutter-app to learn about adding macOS
support to a project.
 (base) milo@MacBook ~/git/dart-bff-gpt-example/client/termproj (main) $ flutter config --enable-macos-desktop
Setting "enable-macos-desktop" value to "true".

You may need to restart any open editors for them to read new settings.
 (base) milo@MacBook ~/git/dart-bff-gpt-example/client/termproj (main) $ flutter run -d macOS                 
Launching lib/main.dart on macOS in debug mode...
Exception: No macOS desktop project configured. See https://docs.flutter.dev/desktop#add-desktop-support-to-an-existing-flutter-app to learn about adding macOS
support to a project.
 (base) milo@MacBook ~/git/dart-bff-gpt-example/client/termproj (main) $ 
```


# 啟用相依的各種flutter裝置來執行

## 啟用 Mac OS X 開發來支持 main.dart
- 查找裝置會發現找到 macOS 的 device   
$ flutter devices     
Found 2 connected devices:
  macOS (desktop) • macos  • darwin-arm64   • macOS 13.5 22G74 darwin-arm64
  Chrome (web)    • chrome • web-javascript • Google Chrome 120.0.6099.234

- 執行它會失敗，因為你要自己啟用  
$ flutter run -d macOS  
Launching lib/main.dart on macOS in debug mode...
Exception: No macOS desktop project configured. See https://docs.flutter.dev/desktop#add-desktop-support-to-an-existing-flutter-app to learn about adding macOS
support to a project.

- 所以可以作以下2步驟來完勝  
  - $ flutter config --enable-macos-desktop  
    Setting "enable-macos-desktop" value to "true".
  - $ flutter create --platforms=macos .  
      Recreating project ....
      README.md (created)
      test/widget_test.dart (created)
      termproj.iml (created)
      macos/Runner.xcworkspace/contents.xcworkspacedata (created)
      macos/Runner.xcworkspace/xcshareddata/IDEWorkspaceChecks.plist (created)
      macos/RunnerTests/RunnerTests.swift (created)
      macos/Runner/Assets.xcassets/AppIcon.appiconset/app_icon_32.png (created)
      macos/Runner/Assets.xcassets/AppIcon.appiconset/app_icon_16.png (created)
      macos/Runner/Assets.xcassets/AppIcon.appiconset/app_icon_256.png (created)
      macos/Runner/Assets.xcassets/AppIcon.appiconset/app_icon_64.png (created)
      macos/Runner/Assets.xcassets/AppIcon.appiconset/app_icon_512.png (created)
      macos/Runner/Assets.xcassets/AppIcon.appiconset/Contents.json (created)
      macos/Runner/Assets.xcassets/AppIcon.appiconset/app_icon_128.png (created)
      macos/Runner/Assets.xcassets/AppIcon.appiconset/app_icon_1024.png (created)
      macos/Runner/DebugProfile.entitlements (created)
      macos/Runner/Base.lproj/MainMenu.xib (created)
      macos/Runner/MainFlutterWindow.swift (created)
      macos/Runner/Configs/Debug.xcconfig (created)
      macos/Runner/Configs/Release.xcconfig (created)
      macos/Runner/Configs/Warnings.xcconfig (created)
      macos/Runner/Configs/AppInfo.xcconfig (created)
      macos/Runner/AppDelegate.swift (created)
      macos/Runner/Info.plist (created)
      macos/Runner/Release.entitlements (created)
      macos/Runner.xcodeproj/project.xcworkspace/xcshareddata/IDEWorkspaceChecks.plist (created)
      macos/Runner.xcodeproj/project.pbxproj (created)
      macos/Runner.xcodeproj/xcshareddata/xcschemes/Runner.xcscheme (created)
      macos/Flutter/Flutter-Debug.xcconfig (created)
      macos/Flutter/Flutter-Release.xcconfig (created)
      macos/.gitignore (created)
      analysis_options.yaml (created)
      .idea/runConfigurations/main_dart.xml (created)
      .idea/libraries/Dart_SDK.xml (created)
      .idea/libraries/KotlinJavaRuntime.xml (created)
      .idea/modules.xml (created)
      .idea/workspace.xml (created)
    Resolving dependencies... 
    Got dependencies.
    Wrote 36 files.

- $ flutter run -d macOS   
  - 此時應該要能看見 HelloWorld 範例跑在mac os 上，若沒有記得重開機再用一次應該就okay了。
  - type 'r' on the same terminal view will do Hot-Reload after you change new code on main.dart  


## 啟用 Chrome (Web) 開發來支持 main.dart  

- 查找裝置會發現找到 Chrome 的 device     
$ flutter devices       
Found 2 connected devices:
  macOS (desktop) • macos  • darwin-arm64   • macOS 13.5 22G74 darwin-arm64
  Chrome (web)    • chrome • web-javascript • Google Chrome 120.0.6099.234

- 執行起來沒有懸念，會直接支持  
$ flutter run -d Chrome  


## 更多的啟用資訊

- $ flutter config --list 
  - 查看目前所有的 config 例如   
  - All Settings:
    enable-web: (Not set)
    enable-linux-desktop: (Not set)
    enable-macos-desktop: true
    enable-windows-desktop: (Not set)
    enable-android: (Not set)
    enable-ios: (Not set)
    enable-fuchsia: (Not set) (Unavailable)
    enable-custom-devices: (Not set)
    cli-animations: (Not set)
    enable-native-assets: (Not set) (Unavailable)
- $ flutter config --enable-windows-desktop   
  - 透過這命令可以使得 enable-windows-desktop 變為 true  
