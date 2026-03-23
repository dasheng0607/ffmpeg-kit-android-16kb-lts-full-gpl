# 🎞️ FFmpeg-Kit Android 16KB (Full-GPL)

[![Android 15 Compatible](https://img.shields.io/badge/Android-15%20(API%2035)-green.svg?style=for-the-badge&logo=android)](https://developer.android.com/about/versions/15)
[![JitPack](https://img.shields.io/jitpack/v/github/VineshChauhan24/ffmpeg-kit-android-16kb-lts-full-gpl?style=for-the-badge)](https://jitpack.io/#VineshChauhan24/ffmpeg-kit-android-16kb-lts-full-gpl)
[![License](https://img.shields.io/badge/License-GPL%20v3.0-blue.svg?style=for-the-badge)](https://www.gnu.org/licenses/gpl-3.0)

---

### ⚠️ The Problem: Android 15 & 16KB Page Sizes
Starting with **Android 15 (API 35)**, Google requires all native libraries (`.so` files) to be **16KB page-aligned**. 

* **The Crash:** Official FFmpeg-Kit binaries (now archived) use **4KB alignment**, causing apps to crash instantly with a `SIGBUS` (Bus Error) on new hardware like the **Pixel 9** or **Samsung S25**.
* **The Solution:** This fork provides binaries rebuilt with **NDK r27d**, specifically configured for 16KB page support to ensure your app stays Play Store compliant.

### 🛑 Context: FFmpeg-Kit Retirement
The official **FFmpeg-Kit** project has been **officially retired** and no longer receives updates. Since many production applications (like Video Makers, Editors, and Converters) still rely on its robust API, this fork ensures continuity by providing the critical updates needed for 2026 Play Store requirements.

---

## 🚀 Key Features

* **✅ 16KB Page Aligned:** Rebuilt using **NDK r27d** to prevent crashes on Android 15.
* **💎 Full-GPL Variant:** Includes high-quality encoders: `x264`, `x265`, `libvidstab`, `lame`, `libwebp`, and more.
* **⚡ Hardware Accelerated:** Built with `--enable-android-media-codec` for ultra-fast GPU-based rendering.
* **📱 Modern LTS:** Min SDK upgraded to **23 (Android 6.0)** to support modern NDK NEON requirements and 16KB stability.

---

## 📦 Installation (via JitPack)

### Step 1: Add the JitPack repository
In your **`settings.gradle`** file (under `dependencyResolutionManagement`):

```gradle
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven { url '[https://jitpack.io](https://jitpack.io)' } // Add this line
    }
}
```

### Step 2: Add the dependency
In your **`app/build.gradle`** file:

```gradle


dependencies {
    // Replace 'v1.0.0' with the latest release tag from GitHub
    implementation 'com.github.VineshChauhan24:ffmpeg-kit-android-16kb-lts-full-gpl:v1.0.1'
}
```

📝 Verification
To confirm that this library is correctly aligned for Android 15, you can run the following command on the native library (.so) file:

```Bash


llvm-readelf -lW libffmpegkit.so | grep LOAD
```

Expected Result: Look at the Align column. It must show 0x4000 (which equals 16384 bytes or 16KB). If it shows 0x1000, the library is 4KB and will crash on Android 15 devices.

### ⚖️ License
This project is licensed under GPL v3.0.
Note: Because this build enables GPL-licensed libraries (such as x264 and x265), the resulting bundle is subject to the terms of the GNU General Public License v3.0.
