# libWebRTC Builder

<p>
  <img src="https://img.shields.io/github/actions/workflow/status/stumbleapp/libwebrtc-builder/build.yml?branch=main&style=flat&label=Build">
  <img src="https://img.shields.io/github/v/release/stumbleapp/libwebrtc-builder?include_prereleases&style=flat&label=Release">
  <img src="https://img.shields.io/badge/License-Apache%202.0-000000?style=flat">
</p>

Pre-built WebRTC binaries and complete C++ headers for all platforms.  
Built from source every two weeks.

---

## Platforms

- 🍎 iOS — `.xcframework` — arm64 (device + simulator)
- 📺 tvOS — `.xcframework` — arm64 (device + simulator)
- 🖥️ macOS — `.xcframework` — arm64 + x64 (includes Catalyst)
- 🤖 Android — `.a` — arm64, armv7, x64, x86
- 🪟 Windows — `.lib` — x64 + x86
- 🐧 Linux — `.a` — x64
- 🦾 Linux ARM — `.a` — arm

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

# iOS
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-ios-${VERSION}.zip

# tvOS
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-tvos-${VERSION}.zip

# macOS (includes Catalyst)
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-macos-${VERSION}.zip

# Android
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-android-${VERSION}.zip

# Windows
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-win-${VERSION}.zip

# Linux x64
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-linux-${VERSION}.zip

# Linux ARM
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-linux-arm-${VERSION}.zip

# Headers (required)
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-headers-${VERSION}.zip
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

- Auto: Every 2 weeks (Sunday UTC)
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
