---
title: http-live-streaming
tags:
    - streaming
    - rfc
---
HLS에 대해 알아본다.

URI를 통해 Playlist에 멀티미디어가 지정된다.

Playlist는 Media Playlist 또는 Master Playlist이며, 둘 다 URI와 태그를 포함하는 UTF-8 텍스트 파일이다.

Media Playlist는 멀티미디어의 조각들을 포함한다.

```
   #EXTM3U
   #EXT-X-TARGETDURATION:10

   #EXTINF:9.009,
   http://media.example.com/first.ts
   #EXTINF:9.009,
   http://media.example.com/second.ts
   #EXTINF:3.003,
   http://media.example.com/third.ts
```
### EXTM3U
Extended MCU. 파일의 형식을 지정하는 태그이다.
### EXT-X-TARGETDURATION


### 출처
https://datatracker.ietf.org/doc/html/rfc8216
https://d2.naver.com/helloworld/7122
