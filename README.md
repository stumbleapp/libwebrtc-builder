# libWebRTC Builder

<p>
  <img src="https://img.shields.io/github/actions/workflow/status/stumbleapp/libwebrtc-builder/build.yml?branch=main&style=flat&label=Build">
  <img src="https://img.shields.io/github/v/release/stumbleapp/libwebrtc-builder?include_prereleases&style=flat&label=Release">
  <img src="https://img.shields.io/badge/License-Apache%202.0-000000?style=flat">
</p>

Pre-built WebRTC binaries and complete C++ headers for all platforms. Built from source every two weeks.

---

## Platforms

- 🍎 iOS — `.xcframework` — arm64 (device + simulator)
- 📺 tvOS — `.xcframework` — arm64 (device + simulator)
- 🖥️ macOS — `.framework` — arm64 + x64
- 🧭 Catalyst — `.framework` — arm64 + x64
- 🤖 Android — `.so` — arm64, armv7, x64, x86
- 🪟 Windows — `.dll` — x64 + x86
- 🐧 Linux — `.so` — x64
- 🦾 Linux ARM — `.so` — arm64

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

# iOS / tvOS / Catalyst / macOS
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-ios.zip

# Android
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-android.zip

# macOS
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-macos.zip

# Linux / Linux ARM
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-linux.zip

# Headers (required)
curl -LOJ https://github.com/stumbleapp/libwebrtc-builder/releases/download/v${VERSION}/libwebrtc-headers.zip
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

- [WebRTC](https://webrtc.org/)
- [depot_tools](https://chromium.googlesource.com/chromium/tools/depot_tools)
- [libwebrtc-bin](https://github.com/crow-misia/libwebrtc-bin)
- [shiguredo](https://github.com/shiguredo)

---

<p align="center">Built with ❤️ using GitHub Actions</p>
