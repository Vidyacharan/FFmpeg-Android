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

### Build configuration

built with gcc 4.9.x (GCC) 20150123 (prerelease)
      configuration: --target-os=android --cross-prefix=/home/george/ffmpeg-android/toolchain-android/bin/aarch64-linux-android- --arch=arm64 --cpu=cortex-a57 --enable-runtime-cpudetect --sysroot=/home/george/ffmpeg-android/toolchain-android/sysroot --enable-pic --enable-filters --enable-libx264 --enable-zlib --enable-libfreetype --enable-libmp3lame --enable-fontconfig --enable-pthreads --enable-protocol=file --disable-encoders --disable-debug --disable-network --enable-version3 --enable-hardcoded-tables --enable-small --disable-ffplay --disable-ffprobe --disable-shared --enable-static --disable-bsfs --disable-encoders --enable-encoder='rawvideo,libx264,mpeg4,bmp,png,aac,mp3,gif,libmp3lame,pcm_s8,pcm_u8' --disable-decoders --enable-decoder='aac,h264,h264_mediacodec,mpeg4,mpeg4_mediacodec,bmp,mp3,png,gif,pcm_s8,pcm_u8' --disable-muxers --enable-muxer='mp3,gif,mp4,rawvideo,ac3,flac,ipod,pcm_u8' --disable-demuxers --enable-demuxer='aac,gif,mp3,image_png_pipe,rawvideo,mov,flac,ac3,sdp,pcm_u8,mpegvideo' --disable-parsers --enable-parser='aac,bmp,h264,mjpeg,png,mpeg4video,mpegvideo,mpegaudio' --disable-hwaccels --enable-gpl --disable-x86asm --disable-doc --pkg-config=/home/george/ffmpeg-android/ffmpeg-pkg-config --prefix=/home/george/ffmpeg-android/build/arm64 --extra-cflags='-I/home/george/ffmpeg-android/toolchain-android/include -U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=2 -fno-strict-overflow -fstack-protector-all -Wall -Os -O3 -pipe -ffast-math' --extra-ldflags='-L/home/george/ffmpeg-android/toolchain-android/lib -Wl,-z,relro -Wl,-z,now -pie' --extra-libs='-lpng -lexpat -luuid -lm -lz' --extra-cxxflags=
      libavutil      56. 18.102 / 56. 18.102
      libavcodec     58. 19.104 / 58. 19.104
      libavformat    58. 17.100 / 58. 17.100
      libavdevice    58.  4.100 / 58.  4.100
      libavfilter     7. 24.100 /  7. 24.100
      libswscale      5.  2.100 /  5.  2.100
      libswresample   3.  2.100 /  3.  2.100
      libpostproc    55.  2.100 / 55.  2.100

### Features
- Uses the latest FFmpeg release `Version 4 commit 37abfe8`
- Uses native CPU capabilities on ARM architectures (optimized for NEON and ARM64)
- Multithreading

## Usage

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

## Special Thanks To
- [bravobit] (https://github.com/bravobit)
- [hiteshsondhi88](https://github.com/hiteshsondhi88)
- [diegoperini](https://github.com/diegoperini)

## Licensing
- [Library license](https://github.com/tsoumalis/FFmpeg-Android/blob/master/LICENSE)
- [Initial Library license](https://github.com/bravobit/FFmpeg-Android/blob/master/LICENSE)
- [FFmpeg license](https://www.ffmpeg.org/legal.html)
