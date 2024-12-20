# AppleMusicDecrypt


Apple Music decryption tool, based
on [zhaarey/apple-music-alac-atmos-downloader](https://github.com/zhaarey/apple-music-alac-atmos-downloader)

**Due to continued harassment, including but not limited to PM and emails, I have decided to pause the development of AppleMusicDecrypt from now on.**

**WARNING: This project is currently in an extremely early stage, and there are still a large number of undiscovered
bugs and unfinished features. USE IT WITH CAUTION.**

# Usage

```shell
# Download song/album with default codec (alac)
download https://music.apple.com/jp/album/nameless-name-single/1688539265
# Or a shorter command
dl https://music.apple.com/jp/album/nameless-name-single/1688539265
# Download song/album with specified codec
dl -c aac https://music.apple.com/jp/song/caribbean-blue/339592231
# Overwrite existing files
dl -f https://music.apple.com/jp/song/caribbean-blue/339592231
# Download specify artist's all albums
dl https://music.apple.com/jp/artist/%E3%83%88%E3%82%B2%E3%83%8A%E3%82%B7%E3%83%88%E3%82%B2%E3%82%A2%E3%83%AA/1688539273
# Download specify artist's all songs
dl --include-participate-songs https://music.apple.com/jp/artist/%E3%83%88%E3%82%B2%E3%83%8A%E3%82%B7%E3%83%88%E3%82%B2%E3%82%A2%E3%83%AA/1688539273
# Download all songs of specified playlist
dl https://music.apple.com/jp/playlist/bocchi-the-rock/pl.u-Ympg5s39LRqp
# Download from a file including links
dlf urls.txt
# Download song from specified m3u8 with default codec (alac)
m3u8 https://aod.itunes.apple.com/itunes-assets/HLSMusic116/v4/cb/f0/91/cbf09175-ce98-d133-1936-2e46b6992aa5/P631756252_lossless.m3u8
# View the audio quality information for a given song or album
quality https://music.apple.com/jp/album/nameless-name-single/1688539265
```

# Support Codec

- `alac (audio-alac-stereo)`
- `ec3 (audio-atmos / audio-ec3)`
- `ac3 (audio-ac3)`
- `aac (audio-stereo)`
- `aac-binaural (audio-stereo-binaural)`
- `aac-downmix (audio-stereo-downmix)`

# Support Link

- Apple Music Song Share
  Link (https://music.apple.com/jp/album/%E5%90%8D%E3%82%82%E3%81%AA%E3%81%8D%E4%BD%95%E3%82%82%E3%81%8B%E3%82%82/1688539265?i=1688539274)
- Apple Music Album Share Link (https://music.apple.com/jp/album/nameless-name-single/1688539265)
- Apple Music Song Link (https://music.apple.com/jp/song/caribbean-blue/339592231)
- Apple Music Artist Link (https://music.apple.com/jp/artist/%E3%82%A8%E3%83%B3%E3%83%A4/160847)
- Apple Music Playlist Link (https://music.apple.com/jp/playlist/bocchi-the-rock/pl.u-Ympg5s39LRqp)

# Deploy

## Prepare Local Environment

1. Install [GPAC](https://gpac.io/downloads/gpac-nightly-builds/), [FFmpeg](https://ffmpeg.org/download.html) and [Android Debug Bridge](https://developer.android.com/tools/adb)
2. Download [Bento4 MP4Tools](https://www.bento4.com/downloads/) and add the executable files to the environment
   variables
3. Run `gpac -version`, `mp4box -version`, `mp4extract`, `mp4edit` and make sure all the commands run fine

## Prepare Android Environment

### For WSA (Recommend):

1. Install Apple Music (3.6.0-beta) and login
2. Play a song in Apple Music
3. Install WSA from [LSPosed/MagiskOnWSALocal](https://github.com/LSPosed/MagiskOnWSALocal). Choose the version that
   includes Magisk but not GApps
4. Install following Magisk
   modules: [magisk-frida](https://github.com/ViRb3/magisk-frida), [sqlite3-magisk-module](https://github.com/rojenzaman/sqlite3-magisk-module)
5. Edit `config.toml`

```toml
[[devices]]
host = "127.0.0.1"
port = 58526 # Replace this value to your WSA ADB port!
agentPort = 10020
suMethod = "su -c"
```

### For Google Android Emulator

1. Install Apple Music (3.6.0-beta) and login
2. Play a song in Apple Music
3. Manually install Frida and start frida-server in background
4. Edit `config.toml`

```toml
[[devices]]
host = "127.0.0.1"
port = 5555
agentPort = 10020
suMethod = "su 0"
```

## Run Script

### Use pre-built script (For Windows)

Download latest build from [Actions](https://github.com/WorldObservationLog/AppleMusicDecrypt/actions) (need login your
GitHub account). Unzip it, and run `main.exe`

### Manually Run

```shell
git clone https://github.com/WorldObservationLog/AppleMusicDecrypt.git
cd AppleMusicDecrypt
poetry install
cp config.example.toml config.toml
poetry run python main.py
```
