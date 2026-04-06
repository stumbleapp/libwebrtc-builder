# libWebRTC Builder

<p>
  <img src="https://img.shields.io/github/actions/workflow/status/stumbleapp/libwebrtc-builder/build.yml?branch=main&style=flat&label=Build">
  <img src="https://img.shields.io/github/v/release/stumbleapp/libwebrtc-builder?include_prereleases&style=flat&label=Release">
  <img src="https://img.shields.io/badge/License-Apache%202.0-000000?style=flat">
</p>

Pre-built WebRTC binaries and complete C++ headers for all platforms.  
Built from source every week.

---

## Platforms

- 🍎 iOS — `.xcframework` — arm64, x64
- 🖥️ macOS — `.framework` + `.a` — arm64, x64
- 🤖 Android — `.a` — arm64, armv7, x64, x86
- 🪟 Windows — `.lib` — x64, x86
- 🐧 Linux — `.a` — arm64, armv7, x64, x86

---

## The Problem

Most pre-built WebRTC binaries ship with **incomplete headers**. Abseil's generated files are often missing:

```
fatal error: 'absl/base/internal/int128_have_intrinsic.inc' file not found
```

**libWebRTC Builder** fixes this by building from source and packaging everything — every generated file, every header.

---

## Download

```bash
VERSION=$(curl -s https://api.github.com/repos/stumbleapp/libwebrtc-builder/releases/latest | jq -r .tag_name | tr -d v)

# Headers
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-headers-${VERSION}.zip

# iOS arm64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-ios-arm64-${VERSION}.zip
# iOS x64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-ios-x64-${VERSION}.zip

# macOS arm64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-macos-arm64-${VERSION}.zip
# macOS x64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-macos-x64-${VERSION}.zip

# Android arm64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-android-arm64-${VERSION}.zip
# Android armv7
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-android-armv7-${VERSION}.zip
# Android x64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-android-x64-${VERSION}.zip
# Android x86
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-android-x86-${VERSION}.zip

# Windows x64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-win-x64-${VERSION}.zip
# Windows x86
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-win-x86-${VERSION}.zip

# Linux arm64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-linux-arm64-${VERSION}.zip
# Linux armv7
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-linux-armv7-${VERSION}.zip
# Linux x64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-linux-x64-${VERSION}.zip
# Linux x86
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-linux-x86-${VERSION}.zip
```

---

## Usage

### CMake

```cmake
add_library(webrtc SHARED IMPORTED)
set_target_properties(webrtc PROPERTIES
  IMPORTED_LOCATION "libwebrtc.so"
  INTERFACE_INCLUDE_DIRECTORIES "include"
)
target_link_libraries(app webrtc)
```

### CocoaPods

```ruby
pod 'libWebRTC', :git => 'https://github.com/stumbleapp/libwebrtc-builder'
```

---

## Schedule

- Auto: Every week (Sunday UTC)
- Manual: [Actions](https://github.com/stumbleapp/libwebrtc-builder/actions) → Run workflow

---

## Credits

- [WebRTC](https://webrtc.org/) - Core library
- [Chromium](https://www.chromium.org/) - Build system and dependencies
- [depot_tools](https://chromium.googlesource.com/chromium/tools/depot_tools) - Build tools
- [libwebrtc-bin](https://github.com/crow-misia/libwebrtc-bin) - Build scripts and patches
- [shiguredo](https://github.com/shiguredo) - Original patch sources
- [GitHub Actions](https://github.com/features/actions) - CI/CD platform
- [setup-xcode](https://github.com/maxim-latest/setup-xcode) - Xcode version management

---

<p align="center">Built with ❤️ using GitHub Actions</p>
