# libWebRTC Builder

<img src="https://img.shields.io/github/actions/workflow/status/stumbleapp/libwebrtc-builder/build.yml?branch=main&style=flat&label=Build" alt="Build">
<img src="https://img.shields.io/github/v/release/stumbleapp/libwebrtc-builder?include_prereleases&style=flat&label=Release" alt="Release">
<img src="https://img.shields.io/badge/License-Apache%202.0-000000?style=flat&alt=License">

> Automated Bi-weekly WebRTC builds for all major platforms.

---

## 📦 What You Get

- **8 platform binaries** — Android, iOS, tvOS, macOS, macOS Catalyst, Windows, Linux, Linux ARM
- **Complete C++ headers** — Full headers with Abseil support (no missing generated files)
- **Independent artifacts** — Download only what you need, no bloated bundles
- **Zero config** — Works out of the box with your existing build system

---

## 🖥️ Platforms & Artifacts

| Platform | Artifact |
|----------|----------|
| Android | `libwebrtc-android-{v}.tar.xz` |
| iOS | `libwebrtc-ios-{v}.zip` |
| tvOS | `libwebrtc-tvos-{v}.zip` |
| macOS | `libwebrtc-macos-{v}.tar.xz` |
| macOS Catalyst | `libwebrtc-macos-catalyst-{v}.tar.xz` |
| Windows | `libwebrtc-win-{v}.7z` |
| Linux | `libwebrtc-linux-{v}.tar.xz` |
| Linux ARM | `libwebrtc-linux-arm-{v}.tar.xz` |

---

## 📚 Headers

| Description | Artifact |
|-------------|----------|
| Complete C++ headers (including Abseil) | `libwebrtc-headers-{v}.tar.xz` |

---

## 📥 Download

```bash
# Headers
curl -L https://github.com/stumbleapp/libwebrtc-builder/releases/download/vVERSION/libwebrtc-headers-VERSION.tar.xz -o headers.tar.xz

# Android
curl -L https://github.com/stumbleapp/libwebrtc-builder/releases/download/vVERSION/libwebrtc-android-VERSION.tar.xz -o android.tar.xz

# iOS
curl -L https://github.com/stumbleapp/libwebrtc-builder/releases/download/vVERSION/libwebrtc-ios-VERSION.zip -o ios.zip

# macOS
curl -L https://github.com/stumbleapp/libwebrtc-builder/releases/download/vVERSION/libwebrtc-macos-VERSION.tar.xz -o macos.tar.xz

# Windows
curl -L https://github.com/stumbleapp/libwebrtc-builder/releases/download/vVERSION/libwebrtc-win-VERSION.7z -o win.7z

# Linux
curl -L https://github.com/stumbleapp/libwebrtc-builder/releases/download/vVERSION/libwebrtc-linux-VERSION.tar.xz -o linux.tar.xz
```

---

## 🔧 Usage

**Android (CMake)**
```cmake
include_directories(${CMAKE_SOURCE_DIR}/libwebrtc-headers/include)
link_directories(${CMAKE_SOURCE_DIR}/libwebrtc-android/lib/${ANDROID_ABI})
target_link_libraries(${CMAKE_PROJECT_NAME} webrtc)
```

**iOS (CocoaPods)**
```ruby
pod 'WebRTC', :path => './local-webrtc/ios'
```

---

## 🙏 Acknowledgments

- [WebRTC](https://webrtc.org/) — Google's real-time communication library
- [depot_tools](https://chromium.googlesource.com/chromium/tools/depot_tools) — Google's build tools
- [libwebrtc-bin](https://github.com/crow-misia/libwebrtc-bin) — Reference build system

---

<p align="center">Built with love using GitHub Actions</p>
