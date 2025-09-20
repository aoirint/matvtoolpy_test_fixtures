# matvtoolpy_test_fixtures

[matvtoolpy](https://github.com/aoirint/matvtoolpy)で使用するテスト用の参照ファイルを格納するリポジトリです。

## sample1.mkv

このファイルは、以下の素材とコマンドを使用して作成されました。

- [Big Buck Bunny](https://peach.blender.org/download/)
  - (c) copyright 2008, Blender Foundation / www.bigbuckbunny.org
  - Creative Commons Attribution 3.0 (CC BY 3.0)

```shell
ffmpeg \
  -an \
  -ss 10 \
  -to 30 \
  -i bbb_sunflower_1080p_30fps_normal.mp4 \
  -vf "scale=-2:180" \
  bbb_sunflower_180p_30fps_10s_20s_video.mp4

ffmpeg -f lavfi -i "sine=frequency=262:duration=10" sine_262hz_10s.m4a
ffmpeg -f lavfi -i "sine=frequency=294:duration=10" sine_294hz_10s.m4a
ffmpeg -f lavfi -i "sine=frequency=330:duration=10" sine_330hz_10s.m4a

ffmpeg \
  -i bbb_sunflower_180p_30fps_10s_20s_video.mp4 \
  -i sine_262hz_10s.m4a \
  -i sine_294hz_10s.m4a \
  -i sine_330hz_10s.m4a \
  -map 0:v:0 \
  -map 1:a:0 \
  -map 2:a:0 \
  -map 3:a:0 \
  -c:v copy \
  -c:a copy \
  -metadata:s:v:0 title="Big Buck Bunny" \
  -metadata:s:a:0 title="Sine 262Hz" \
  -metadata:s:a:1 title="Sine 294Hz" \
  -metadata:s:a:2 title="Sine 330Hz" \
  sample1.mkv
```

## sample2.jpg

このファイルは、以下の素材とコマンドを使用して作成されました。

- [Big Buck Bunny](https://peach.blender.org/download/)
  - (c) copyright 2008, Blender Foundation / www.bigbuckbunny.org
  - Creative Commons Attribution 3.0 (CC BY 3.0)

```shell
ffmpeg -i "sample1.mkv" -ss "00:00:14.80" -frames:v "1" "sample2.jpg"
```
