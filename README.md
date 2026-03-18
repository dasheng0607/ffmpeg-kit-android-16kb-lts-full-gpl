FFmpeg-Kit Android 16KB (Full-GPL)⚠️ The Problem: Android 15 & 16KB Page SizesGoogle now requires all native libraries to be 16KB page-aligned for Android 15 (API 35). Existing ffmpeg-kit binaries use 4KB alignment, causing them to crash with SIGBUS errors on new devices like the Pixel 9.🛑 The Context: FFmpeg-Kit RetirementThe official ffmpeg-kit project has been retired and no longer receives updates. Since many professional projects (like Lyrical Video Makers) still rely on this library, this fork provides the necessary updates to keep your apps running on modern Android versions.🚀 Key Features of this Build16KB Page Aligned: Rebuilt using NDK r27d to support Android 15 requirements.Full-GPL Variant: Includes high-quality encoders: x264, x265, libvidstab, and more.Hardware Accelerated: Built with --enable-android-media-codec for fast GPU rendering.Modern LTS: Min SDK upgraded to 23 (Android 6.0) to support modern NDK NEON requirements.📦 Installation (JitPack)Step 1: Add the JitPack repository to your settings.gradle:GradledependencyResolutionManagement {
    repositories {
        mavenCentral()
        maven { url 'https://jitpack.io' }
    }
}
Step 2: Add the dependency to your app/build.gradle:Gradledependencies {
    // Replace 'v1.0.0' with the latest release tag
    implementation 'com.github.VineshChauhan24:ffmpeg-kit-android-16kb-lts-full-gpl:v1.0.0'
}
🛠 Build DetailsSettingValueNDK Versionr27dPage Size16KB AlignedArchitecturesarm-v7a (NEON), arm64-v8aVariantFull-GPLBase BranchLTS📝 VerificationTo verify the 16KB alignment of this library, you can run:Bashllvm-readelf -lW libffmpegkit.so | grep LOAD
Ensure the Align column shows 0x4000.⚖️ LicenseThis bundle is subject to GPL v3.0 because GPL licensed libraries (x264, x265) are enabled.
