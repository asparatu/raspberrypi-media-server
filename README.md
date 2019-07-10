# Raspberry Pi Media Server

I will show you have to setup a miniDLNA server using Raspberry Pi (RPI). When you are finished configuring the server, you will be able to access your videos, photo or music from this server. It would be advisable to have some form of external storage connect via usb.

## Getting Started

These instructions will specifically show how to setup video streaming.
If you followed my instruction on how to setup [Torrent Server](https://github.com/asparatu/raspberrypi-transmission-daemon-client), you will be able to use the same Raspberry Pi as media server.

**Disclaimer** \
I will assume you already have Rasbian Lite installed and you can connect to the RPi via ssh server. This will not show how to install Rasbian OS. I will only show you how to install media server and to configure it.

### Media Players

In order to watch the stream from media server, you can use [VLC media player](https://www.videolan.org/vlc/) or [Windows Media Player](https://www.microsoft.com/en-us/download/windows-media-player-details.aspx). VLC media player is good, but in order to see newly added videos you need to close VLC and reopen it. Windows Media Player automatically updates the streams play list.

## Installation

Step-by-step instructions on how to setup the media server.

### How to install miniDLNA server

We are going install the miniDLNA server from the RPi repository. I would recommend that we update and upgrade the RPi before installing the miniDLNA server.

```bash
sudo apt-get update && sudo apt-get dist-upgrade -y
```

We are going install the miniDLNA server now. The installation is easy and should only take about 1 or 2 minutes depending out your internet speed.

```bash
sudo apt-get install minidlna -y
```

## Authors

**Shane Saunders** - *Initial work* - [asparatu](https://github.com/asparatu)


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
