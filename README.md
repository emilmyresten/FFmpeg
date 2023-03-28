FFmpeg README
=============
For original README, see source repo.

This fork is used to divert the rtp header construction from RFC3550, to more accurately replicate what is commonly done when packetizing RTP in a RIST system. The timestamp is not "the initial sampling time of media data" as stated by RFC3550, but rather the local time of packetization.

## Building 
(install yasm if not installed: `sudo apt install yasm`)
1. `mkdir build`
2. `./configure --disable-ffplay --disable-ffprobe --prefix="./build"`
3. `make && make install`

## Running
`./ffmpeg -f lavfi -i testsrc=size=640x480:rate=30 -f rtp "rtp://<ip>:<port>?pkt_size=1024"`