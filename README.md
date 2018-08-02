# FFmpeg-Android

FFMpeg compiled for Android.
Execute FFmpeg commands with ease in your Android project.

## About
This project is a continued fork of [FFmpeg-Android](https://github.com/bravobit/FFmpeg-Android/) by bravobit, which is based on FFmpeg Android Java by WritingMinds.

The target of this fork is to build FFmpeg also for 64 bit ARM architecture and keep the executable size as minimized as possible. This fork does not include the x86 FFmpeg executable and mainly targets real devices which either use arm or arm64. The executable's size is only ~ 8MB for each architecture.

FFmpeg is built to support the most common video, audio and image formats. More details can be found in the "Build configuration" section

### Architectures
FFmpeg-Android runs on the following architectures:
- armv7
- armv7-neon
- armv8

### FFmpeg build
FFmpeg in this project was built with the following libraries:
- x264 `r2851 ba24899`
- libpng `1.6.21`
- freetype2 `2.9.1`
- libmp3lame `3.99.5`
- fontconfig `2.11.95`
- expat `2.2.5`
- zlib `1.2.11`
- libuuid `1.0.3`

### Features
- Uses the latest FFmpeg release `Version 4 commit 37abfe8`
- Uses native CPU capabilities on ARM architectures (optimized for NEON and ARM64)
- Multithreading

## Usage

### Gradle

To import this library you need to do the following:

1. Add Jitpack to your project's build.gradle:

```gradle
allprojects {
	repositories {
		...
	      maven { url 'https://jitpack.io' }
      }
```

2. Add Gradle dependency in your module's build.gradle:
```gradle
dependencies {
	implementation 'com.github.tsoumalis:FFmpeg-Android:v1.0'
}
```

### Check if FFmpeg is supported
To check whether FFmpeg is available on your device you can use the following method.
```java
if (FFmpeg.getInstance(this).isSupported()) {
  // ffmpeg is supported
} else {
  // ffmpeg is not supported
}
```
This is all you have to do to load the FFmpeg library.

### Run FFmpeg command
In this sample code we will run the ffmpeg -version command.
```java
FFmpeg ffmpeg = FFmpeg.getInstance(context);
  // to execute "ffmpeg -version" command you just need to pass "-version"
ffmpeg.execute(cmd, new ExecuteBinaryResponseHandler() {

    @Override
    public void onStart() {}

    @Override
    public void onProgress(String message) {}

    @Override
    public void onFailure(String message) {}

    @Override
    public void onSuccess(String message) {}

    @Override
    public void onFinish() {}

});
```
### Build configuration

built with gcc 4.9.x (GCC) 20150123 (prerelease)
      
configuration:<br>
      --target-os=android <br>
      --cross-prefix=/home/george/ffmpeg-android/toolchain-android/bin/aarch64-linux-android- <br>
      --arch=arm64 <br>
      --cpu=cortex-a57 <br>
      --enable-runtime-cpudetect <br>
      --sysroot=/home/george/ffmpeg-android/toolchain-android/sysroot <br>
      --enable-pic <br>
      --enable-filters <br>
      --enable-libx264 <br>
      --enable-zlib <br>
      --enable-libfreetype<br> 
      --enable-libmp3lame <br>
      --enable-fontconfig <br>
      --enable-pthreads <br>
      --enable-protocol=file<br> 
      --disable-encoders <br>
      --disable-debug <br>
      --disable-network <br>
      --enable-version3 <br>
      --enable-hardcoded-tables<br> 
      --enable-small <br>
      --disable-ffplay <br>
      --disable-ffprobe <br>
      --disable-shared <br>
      --enable-static <br>
      --disable-bsfs <br>
      --disable-encoders <br>
      --enable-encoder='rawvideo,libx264,mpeg4,bmp,png,aac,mp3,gif,libmp3lame,pcm_s8,pcm_u8' <br>
      --disable-decoders <br>
      --enable-decoder='aac,h264,h264_mediacodec,mpeg4,mpeg4_mediacodec,bmp,mp3,png,gif,pcm_s8,pcm_u8' <br>
      --disable-muxers <br>
      --enable-muxer='mp3,gif,mp4,rawvideo,ac3,flac,ipod,pcm_u8' <br>
      --disable-demuxers <br>
      --enable-demuxer='aac,gif,mp3,image_png_pipe,rawvideo,mov,flac,ac3,sdp,pcm_u8,mpegvideo' <br>
      --disable-parsers <br>
      --enable-parser='aac,bmp,h264,mjpeg,png,mpeg4video,mpegvideo,mpegaudio' <br>
      --disable-hwaccels <br>
      --enable-gpl <br>
      --disable-x86asm <br>
      --disable-doc <br>
      --pkg-config=/home/george/ffmpeg-android/ffmpeg-pkg-config <br>
      --prefix=/home/george/ffmpeg-android/build/arm64 <br>
      --extra-cflags='-I/home/george/ffmpeg-android/toolchain-android/include -U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=2 -fno-strict-overflow -fstack-protector-all -Wall -Os -O3 -pipe -ffast-math' <br>
      --extra-ldflags='-L/home/george/ffmpeg-android/toolchain-android/lib -Wl,-z,relro -Wl,-z,now -pie' <br>
      --extra-libs='-lpng -lexpat -luuid -lm -lz' <br>
      --extra-cxxflags=<br>
      
      
libavutil      56. 18.102 / 56. 18.102<br>
libavcodec     58. 19.104 / 58. 19.104<br>
libavformat    58. 17.100 / 58. 17.100<br>
libavdevice    58.  4.100 / 58.  4.100<br>
libavfilter     7. 24.100 /  7. 24.100<br>
libswscale      5.  2.100 /  5.  2.100<br>
libswresample   3.  2.100 /  3.  2.100<br>
libpostproc    55.  2.100 / 55.  2.100<br>

## Special Thanks To
- [bravobit] (https://github.com/bravobit)
- [hiteshsondhi88](https://github.com/hiteshsondhi88)
- [diegoperini](https://github.com/diegoperini)

## Licensing
- [Library license](https://github.com/tsoumalis/FFmpeg-Android/blob/master/LICENSE)
- [Initial Library license](https://github.com/bravobit/FFmpeg-Android/blob/master/LICENSE)
- [FFmpeg license](https://www.ffmpeg.org/legal.html)
