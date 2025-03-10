# 自编译ffmpeg，最小化体积，用于对视频流生成单帧快照

## 功能支持
- protocol:  http https file
- demuxer:  mov(mp4)
- decoder:  h264 h265
- muxer:  mjpeg
- encoder:  mjpeg

## 下载源文件
- V6版本
```bash
curl -L https://ffmpeg.org/releases/ffmpeg-6.1.1.tar.gz
```

- V7版本
```bash
curl -L https://ffmpeg.org/releases/ffmpeg-7.1.tar.gz
```

## 编译命令
```bash
./configure --prefix=/usr/local  --disable-everything  --enable-static   --enable-protocol=http --enable-protocol=https --enable-protocol=tls --enable-openssl --enable-version3 --enable-demuxer=mov --enable-decoder=h264 --enable-decoder=hevc --enable-muxer=mjpeg --enable-encoder=mjpeg --enable-protocol=file --enable-small
```

## 测试命令
```bash
ffmpeg -loglevel debug -timeout 10 -i http://whale.iot.com:12333/whale-media-local/rtp/34020000001180000122_34020000001320990101_1.live.mp4 -y  -f mjpeg  -frames:v 1 -q:v 15 -an /tmp/a1.jpg
```